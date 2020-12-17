[![Gitter chat](http://img.shields.io/badge/gitter-join%20chat%20%E2%86%92-brightgreen.svg)](https://gitter.im/openzipkin/zipkin)
[![Build Status](https://github.com/openzipkin/docker-java/workflows/test/badge.svg)](https://github.com/openzipkin/docker-java/actions?query=workflow%3Atest)

`ghcr.io/openzipkin/java` is a minimal Docker image based on [azul/zulu-openjdk-alpine](https://hub.docker.com/r/azul/zulu-openjdk-alpine).

GitHub Container Registry: [ghcr.io/openzipkin/java](https://github.com/orgs/openzipkin/packages/container/package/java) includes:
 * `MAJOR.MINOR.PATCH` tag: release corresponding to the java version

## Using this image
This is an internal base layer primarily used in [zipkin](https://github.com/openzipkin/zipkin).

To try the image, run the `java -version` command:
```bash
docker run --rm ghcr.io/openzipkin/java:1.6.0-119 -version
openjdk version "1.6.0-119"
OpenJDK Runtime Environment (Zulu 6.22.0.3-linux64) (build 1.6.0-119-b119)
OpenJDK 64-Bit Server VM (Zulu 6.22.0.3-linux64) (build 23.77-b119, mixed mode)
```

## Release process
Build the `Dockerfile`
```bash
./build-bin/build
```

Next, verify the built image matches that version:
```bash
docker run --rm openzipkin/java:test -version
openjdk version "1.6.0-119"
OpenJDK Runtime Environment (Zulu 6.22.0.3-linux64) (build 1.6.0-119-b119)
OpenJDK 64-Bit Server VM (Zulu 6.22.0.3-linux64) (build 23.77-b119, mixed mode)
```

To release the image, push a tag matching the arg to `build-bin/build` (ex `1.6.0-119`).
This triggers a [GitHub Actions](https://github.com/openzipkin/docker-java/actions) job to push the image.
