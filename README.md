# Kuvera Unofficial API Specification

Please see https://captnemo.in/kuvera-unofficial-api-specification/

## Terms of Service

I'm not responsible. Use at your own risk. This is a read only API, so you can't use this to manage your funds.

## Clients

Generate the Python client by running:

    docker run --rm -v "$PWD":/local openapitools/openapi-generator-cli generate -c /local/openapi-generator-config.yml  -i /local/reference/Kuvera.yaml -o /local/src/python -g python

The generated client is currently broken due to bugs in openapi-generator which misses a few imports.

## For SP

```
docker run --rm -v "$PWD":/local openapitools/openapi-generator-cli generate -i /local/Kuvera.yaml -o /local/src/php -g php  --skip-validate-spec
```
Move the files from src/lib to the destination and as per the destination modify this find and replace
```
find . -name "*.php" -exec sed -i "s/OpenAPI\\\\Client/Apps\\\\Fintech\\\\Packages\\\\Apis\\\\Providers\\\\Kuvera/g" {} +
```