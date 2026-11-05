# ft_irc

*This project was developed collaboratively as part of the 42 curriculum.*

## Description

`ft_irc` is a simplified IRC (Internet Relay Chat) server implemented in **C++98**, following the principles of the IRC protocol defined in RFC 1459.

The server allows multiple clients to connect, authenticate, register, exchange private messages, and communicate through channels using standard IRC commands.

The project focuses on network programming, TCP socket management, non-blocking I/O, event-driven architecture, and object-oriented programming.

## Features

### Server and Networking
- TCP server supporting multiple client connections.
- Non-blocking sockets.
- Event-driven I/O using `epoll()`.
- Client connection and disconnection management.
- Buffered message reception and transmission.

### Authentication and Registration
- Password authentication (`PASS`).
- Nickname registration (`NICK`).
- User registration (`USER`).
- Registration validation before using regular commands.

### Messaging
- Private messages between users (`PRIVMSG`).
- Messages broadcast to channel members.
- IRC-style message formatting and server replies.

### Channel Management
- Create and join channels (`JOIN`).
- Leave channels (`PART`).
- Channel operator privileges.
- Invite users (`INVITE`).
- Remove users (`KICK`).
- Manage channel topics (`TOPIC`).
- Configure channel modes (`MODE`):
  - `i`: Invite-only channel.
  - `t`: Restrict topic changes to operators.
  - `k`: Channel password.
  - `l`: Maximum number of members.
  - `o`: Grant or remove operator privileges.

### Additional Feature
- Built-in IRC bot supporting:
  - `:help` — Display available bot commands.
  - `:time` — Display the current server time.
  - `:upper` — Convert a message to uppercase.

## Architecture

The project separates server logic, socket handling, channel management, and command handling into dedicated components.

- **Server:** Manages connected clients, channels, command dispatching, and the event loop.
- **ListenSocket:** Creates the listening TCP socket and accepts incoming connections.
- **ClientSocket:** Manages individual client connections, registration information, and message buffers.
- **Channel:** Maintains channel members, operators, invitations, modes, topics, and passwords.
- **ISocket:** Defines the common socket interface.
- **IServerContext:** Provides the interface through which sockets interact with the server.
- **Command Handlers:** Implement authentication, messaging, and channel-related commands.

The server uses `epoll()` to monitor socket events and handle multiple connections through a single event loop.

## Technologies and Concepts

- C++98
- TCP/IP
- Socket Programming
- Non-blocking I/O
- `epoll()`
- IRC Protocol (RFC 1459)
- Object-Oriented Programming
- STL (`std::map`, `std::set`, `std::vector`)
- Linux

## Requirements

- Linux environment
- C++ compiler supporting C++98
- Make

## Installation and Usage

Clone the repository:

```bash
git clone https://github.com/sakiSOF1/IRC.git
cd IRC
```

Compile the server:

```bash
make
```

Start the server with a port and connection password:

```bash
./ircserv 6667 password
```

### Connecting with an IRC Client

You can connect using an IRC client such as HexChat.

Configure the server with:

```text
Host: localhost
Port: 6667
```

After connecting, register using IRC commands:

```irc
PASS password
NICK Alice
USER alice 0 * :Alice
```

## Supported Commands

| Command | Description |
|---|---|
| PASS | Authenticate with the server |
| NICK | Set or change a nickname |
| USER | Register user information |
| JOIN | Join a channel |
| PART | Leave a channel |
| PRIVMSG | Send private or channel messages |
| QUIT | Disconnect from the server |
| PING | Check server responsiveness |
| TOPIC | View or change a channel topic |
| MODE | Manage channel modes and operator privileges |
| INVITE | Invite a user to a channel |
| KICK | Remove a user from a channel |

## Resources

- [RFC 1459 — Internet Relay Chat Protocol](https://www.rfc-editor.org/rfc/rfc1459)
- [Linux `epoll` documentation](https://man7.org/linux/man-pages/man7/epoll.7.html)
- [IRC Numeric Replies](https://www.alien.net.au/irc/irc2numerics.html)
- Linux socket programming documentation.

## AI Usage

Artificial intelligence was used as a learning and documentation assistant to help understand networking concepts, the IRC protocol, `epoll()`, C++ features, and debugging issues.

Project design decisions, implementation, testing, and final code integration were completed by the project authors.
