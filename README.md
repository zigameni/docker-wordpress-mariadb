# WordPress Docker Compose Setup

This repository contains a Docker Compose configuration to quickly set up a WordPress website with a MariaDB database using Docker.

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Getting Started

1. Clone this repository to your local machine:

```bash
    git clone https://github.com/zigameni/docker-wordpress-mariadb.git
    cd docker-wordpress-mariadb
```
## Customize your WordPress configuration

Edit the `wordpress1/wp-config.php` file to match your specific WordPress configuration. You can use your preferred text editor to modify the file. Below is an example of how you might edit the file:

```bash
    nano wordpress1/wp-config.php
```
## Run the Docker Compose command to start the services:

```bash
    docker-compose up -d
```
## Access your WordPress site:
Open your web browser and navigate to http://localhost:8080

Access phpMyAdmin at http://localhost:8081 with the credentials:

    Username: root
    Password: root

## Configuration Details

- **WordPress Container:**
  - Image: `wordpress:latest`
  - Port: `8080`
  - WordPress configuration volume: `./wordpress1`
  - WordPress database details:
    - Host: `db`
    - Database: `wordpress`
    - User: `ziga`
    - Password: `ziga`

- **MariaDB Container:**
  - Image: `mariadb:latest`
  - Port: Database is not exposed to the host
  - Database volume: `db_data`
  - Root user password: `root`
  - WordPress database details:
    - Database: `wordpress`
    - User: `ziga`
    - Password: `ziga`

- **phpMyAdmin Container:**
  - Image: `phpmyadmin/phpmyadmin`
  - Port: `8081`
  - Access at [http://localhost:8081](http://localhost:8081)
  - Database details:
    - Host: `db`
    - User: `root`
    - Password: `root`

## Notes

- The WordPress configuration file is mounted from `./wordpress1/wp-config.php`. Customize this file according to your needs.
- This setup is for development purposes. Ensure to secure your production environment appropriately.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
