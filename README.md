# Tutorial 8 - Subscriber

## Reflection
a. What is ***amqp***?

***amqp*** stands for Advanced Message Queuing Protocol, which is designed to facilitate communication between client applications and server applications through middleware-based data transmission. This middleware serves as a data interface needed by the client.

b. What it means? guest:guest@localhost:5672 , what is the first quest, and what is
the second guest, and what is localhost:5672 is for?

`guest:guest@localhost:5672` refers to a set of credentials and connection details used for authentication and network communication. 
- `guest` (first): the username required for authentication
- `guest`(second): the password
- `localhost`: signifies the hostname or IP address of the machine on which the communication is to take place
- `5672`: the port number where the communication will occur

## Simulation slow subscriber

The total number of queues reached approximately 20. This was because the `cargo run` command was executed five times, which ideally should have been carried out over 20 seconds (5 messages per run x 5 runs). However, since the `cargo run` was performed sequentially, there was a delay, resulting in only a maximum of 20 messages being queued at any one time.

<img width="1512" alt="Screenshot 2024-04-23 at 01 18 57" src="https://github.com/rachelzn/tutorial8-subscriber/assets/92985397/d6b4e1dc-9376-4775-bf13-84e26fa73f97">

I executed `cargo run` five times and the reduction in the message queue spike is now faster than before. This improvement is attributed to the subscriber implementing multithreading to handle the communication events sent by the publisher, enabling parallel processing. As for further enhancement, parallelism can be introduced on the publisher's side to send multiple requests simultaneously, providing a more accurate simulation of high traffic scenarios.

<img width="1512" alt="Screenshot 2024-04-23 at 01 46 50" src="https://github.com/rachelzn/tutorial8-subscriber/assets/92985397/bd406b4b-b81e-47cf-b598-e6acc813f8c4">
