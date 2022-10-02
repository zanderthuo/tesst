# Setting up a MQTT bridge
What is MQTT bridge? A MQTT bridge lets you connect two MQTT brokers together.
                     They are generally used for sharing messages between systems.
                     A common usage is connect edge MQTT brokers to a central or remote MQTT network(google).

On this project I will show you how to create a MQTT Bridge for a client broker(client-mqtt-broker)
which will be bridging to the central or remote MQTT Broker(Mqtt-Protected)

## How to configure a MQTT bridge for a client broker.
On this section, I will show you the configurations for creating a MQTT bridge for a specific distributor as a client broker.
You should have an existing distributor account on the ERM to be able to create a MQTT bridge for a client broker.

The below is the snippet for creating a MQTT bridge for client bridge which should be added in the mosquitto.conf file for a broker. 

```sh
# =================================================================
# All Configs Start
# =================================================================

listener 1884

connection testing-bridge
address mqtt-2.omnivoltaic.com:8883
topic # both 0

allow_anonymous true

bridge_cafile /mqtt_client_broker1/config/ca.crt
bridge_certfile /mqtt_client_broker1/config/client.crt
bridge_keyfile /mqtt_client_broker1/config/client.key
bridge_insecure false

remote_username Kevin Kibet
remote_password null

tls_version tlsv1.2

# =================================================================
# All Configs End
# =================================================================

```

The below is the snippet for creating a MQTT bridge for Edge/Hub(Termux) Layer bridge which should be added in the mosquitto.conf file for a broker.
The broker will bridge to one of the client brokers.

```sh
# =================================================================
# All Configs Start
# =================================================================

listener 1884

connection testing-bridge2
address mqtt-2.omnivoltaic.com:1885
topic # both 0

allow_anonymous true

# =================================================================
# All Configs End
# =================================================================

```