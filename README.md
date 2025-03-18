# For Your take-home coding challenge

Please create docker service running `nginx` web server. Complete as many tasks as possible. Feel free to skip one or many tasks (either whole step or particular sub bullet point). Use `git` to commit your results afer each completed step (this directory already contains git repository).

1. Create a nginx web server container using docker compose
    - use official [docker image](https://hub.docker.com/_/nginx)
    - serve different response (static text file) based on `Host` header
        - for example reply `foo` for a request to `http://foo.example.com` and reply `bar` for a request to `http://bar.example.com`
        - you can modify hosts file on your host OS to have basic DNS resolution
1. Produce JSON formatted logs
    - nginx be default writes logs in plain text format. Please convert that to JSON where each log line is one JSON object
    - write those logs to a file in a mounted volume (additionally to stdout/stderr)
    - Create a script/command/function that filters through JSON logs and prints logs where request `Host` header does not equal to TLS SNI value
        - Consider using [jq](https://jqlang.org/) for this
1. Enable TLS
    - generate self-signed certificates using `openssl`
    - serve different response (static text file) based on TLS SNI
    - treat private keys as a secret
1. Add docker container healthcheck
    - check if web server is responding
    - make server not log healthcheck requests
1. Convert this to docker swarm service
    - one node local cluster is sufficient.
    - make service highly available (no downtime during service restart).
