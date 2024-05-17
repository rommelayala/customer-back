# Imagen base
FROM maven:3.8.3-openjdk-17-slim AS build

# Crea un usuario y grupo sin privilegios
RUN addgroup /g 1028 devopsc \
        && adduser -D -G devopsc admin

VOLUME [ "/tmp" ]

# Argumento para el archivo JAR
ARG JAR_FILE

#creamos un argumento para el passw
ARG ARG DB_PASSWORD
# Copia el jar del build
COPY ${JAR_FILE} /tmp/app.jar

#usamos el pass pasado como parametro
ENV DB_PASSWORD=$DB_PASSWORD

RUN chown -R admin:devopsc /tmp

USER admin

# Comando de ejecución
CMD ["java", "-jar", "/app.jar"]
