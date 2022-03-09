# Mule MQTT Mosquitto Example
Example on how to send/consume MQTT messages using Mosquitto Broker

## Get Started - How to Run it

1. Install Mosquitto (Follow steps here https://mosquitto.org/download/)
2. Run Mosquitto broker, using the verbose mode -v
3. Check the logs, that everything is correct and running

```
./mosquitto -v
1646774443: mosquitto version 2.0.14 starting
1646774443: Using default config.
1646774443: Starting in local only mode. Connections will only be possible from clients running on this machine.
1646774443: Create a configuration file which defines a listener to allow remote access.
1646774443: For more details see https://mosquitto.org/documentation/authentication-methods/
1646774443: Opening ipv4 listen socket on port 1883.
1646774443: Opening ipv6 listen socket on port 1883.
1646774443: mosquitto version 2.0.14 running
1646774499: New connection from 127.0.0.1:54230 on port 1883.
1646774499: New client connected from 127.0.0.1:54230 as mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 (p2, c1, k30).
1646774499: No will message specified.
1646774499: Sending CONNACK to mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 (0, 0)
1646774499: Received SUBSCRIBE from mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063
1646774499: 	queue.mule (QoS 1)
1646774499: mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 1 queue.mule
1646774499: Sending SUBACK to mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063
1646774521: Received PUBLISH from mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 (d0, q1, r0, m2, 'queue.mule', ... (63 bytes))
1646774521: Sending PUBLISH to mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 (d0, q1, r0, m1, 'queue.mule', ... (63 bytes))
1646774521: Sending PUBACK to mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 (m2, rc0)
1646774521: Received PUBACK from mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 (Mid: 1, RC:0)
1646774551: Received PINGREQ from mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063
1646774551: Sending PINGRESP to mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063
1646774560: Client mule-mosquitto-client22-56d1f126-1f1a-4e4b-ba88-156168b06063 closed its connection.
^C1646774671: mosquitto version 2.0.14 terminating
```

4. Set initial mosquitto config (modify file at /usr/local/etc/mosquitto/mosquitto.conf)

```
# Unencrypted MQTT over TCP
# for listener at port 1883
listener 1883
allow_anonymous true
# =================================================================
# Logging
# =================================================================
# Route log messages to log file
log_dest file /mosquitto/mosquitto.log
# Types of messages to log. Use multiple log_type lines for logging
# multiple types of messages.
log_type debug
log_type error
log_type warning
log_type notice
log_type information
```

5. Import this code into the Anypoint Studio and run it (it's working with the defauflt Mosquitto configuration)

### Troubleshooting

As mentioned here: https://github.com/micropython/micropython-lib/issues/445#issuecomment-1041223939
Now the connection configuration needs a keep alive interval value greater than 0, set it to 30 sec.


### References
- http://www.steves-internet-guide.com/mosquitto-broker/
