# PHP, MariaDB, and Nginx with Docker

This repository provides a Docker setup for running a PHP application with MariaDB and Nginx.

## Getting Started

Follow these instructions to get your PHP application up and running with Docker.

### Prerequisites

Make sure you have Docker and Docker Compose installed on your machine.

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Setup

1. **Clone the Repository**:

   ```sh
   git clone https://github.com/teknik-github/php-mariadb-nginx-docker.git
   cd php-mariadb-nginx-docker
   ```

2. **Add Your PHP Application**:

   Copy your PHP application into the `web` folder of the repository.

3. **Start Docker Containers**:

   Run the following command to start the Docker containers:

   ```sh
   docker-compose up -d
   ```

4. **Access the Application**:

   Open your web browser and go to [http://localhost](http://localhost) or use your server's IP address to see your PHP application.

### Database Configuration

In your PHP application, use the hostname `db` to connect to the MariaDB database. Here is an example of how to configure the database connection in PHP:

```php
<?php
$servername = "db";  // Use the service name defined in Docker Compose
$username = "root";
$password = "1234";

try {
  $conn = new PDO("mysql:host=$servername;dbname=curd", $username, $password);
  // set the PDO error mode to exception
  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  echo "Connected successfully";
} catch(PDOException $e) {
  echo "Connection failed: " . $e->getMessage();
}
?>
```

### Folder Structure

- `web`: This folder should contain your PHP application.

### Docker Services

- **Nginx**: The web server serving your PHP application.
- **MariaDB**: Database service for the application.

### Docker Volumes

- `mariadb_data`: Persistent storage for MariaDB data.

### Environment Variables

The Docker Compose file sets the following environment variables for the MariaDB service:

- `MARIADB_ROOT_PASSWORD=1234`
- `MARIADB_DATABASE=curd`

You can customize these variables in the `docker-compose.yml` file if needed.

### Troubleshooting

If you encounter any issues, check the logs of the Docker containers:

```sh
docker-compose logs -f
```

## Contributing

Contributions are welcome! Please fork this repository and submit a pull request with your improvements.
