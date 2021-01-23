# docker-airflow
A simple Apache Airflow environment using Docker and Docker Compose.


# Environment construction procedure

1. **Clone this repository** to a directory of your choice.
1. **Move** to the `docker-airflow` directory
1. **Switch branches** according to the repository DB type
    - SQLite: Use the `main` branch
    - PostgreSQL: Use the `repos-postgres` branch
    - MySQL: Use the `repos-mysql` branch
1. **Change the command** in the `webserver` container to `db init`
1. **Run** `docker-compose up` to initialize the DB and exit with` Ctrl + C` when complete
1. **Change the command** in the `webserver` container to `webserver`
1. **Run** `docker-compose up -d`
1. Create an Airflow admin user
1. **Access** `http://127.0.0.1:8080` with a web browser and log in to Airflow

## Creating an admin user

You can create a user by running the Airflow CLI in the `webserver` container as shown below.  

```bash:example
docker-compose run --rm webserver airflow users create \
    --username admin \
    --firstname Peter \
    --lastname Parker \
    --role Admin \
    --email spiderman@superhero.org
```

For more information on the command, see the [official Apache Airflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/cli-and-env-variables-ref.html#create_repeat1).
