## Find Wifes Phone

The container will connect to a message queue, and subscribe to a specified topic. Then whenever a message is published the service will log into icloud, and perform a find my iphone.

You **must** provide the following environmental variables:

* BROKER - the ip or hostname of the mqtt server
* CLIENT_ID - the client id reported to the broker (also reported to Apple, but that doesn't appear to be significant)
* APPLE_USERNAME - your apple username
* APPLE_PASSWORD - your apple password

You may optionally provide the following:

* MQTT_USERNAME - a username for the message broker
* MQTT_PASSWORD - a password for the broker
* MQTT_TOPIC - the topic you would like to subscribe to (if none is provided the application will default to /findphone)

# Docker-Compose details

    findwifesphone:
      image: rossdargan/findwifesphone
      environment:
        - BROKER=x.x.x.x
        - CLIENT_ID=myclient
        - APPLE_USERNAME=appleseed@apple.me
        - APPLE_PASSWORD=some strong password


# Outstanding issues
* Currently there is no way to specify the port for the message broker
* If you have more than 1 device named the same then we will just perform the search on the first one.
* You will be e-mailed every time this performs a find my phone
* This is not a trusted build as I haven't made that work yet. This means you don't really know what code is inside the application. Please build it yourself to be safe!
