# home-minio
Internal Minio service - used for local backup

## Running
Everything is in `docker-compose.yml` including the admin client `mc`.

Before running -

* Copy `minio.env.example` to `minio.env` and edit the environment variables
* Add storage using `docker volume create`, e.g., loopback mount to local
  storage
* Edit the Traefik config in `docker-compose.yml`

To run -
* `docker compose up -d`

## Admin
`mc` or the web client can be used to admin the instance. Use
`docker compose run mc --help` for more info. This container will be on the
same network as the Minio service so can use the service names as hostnames
to access the minio API.

For example -
* `docker compose run mc alias set myminio http://minio:9000 root 'myrootkey'`
* `docker compose run mc admin info myminio`

