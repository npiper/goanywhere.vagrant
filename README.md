# GoAnywhere install

This is Vagrant image to install RHEL/Centos7 + GoAnywhere

It will self-install go anywhere with a scripted install to respond to prompts.

There are 2 variants:

1) AWS (Default)
2) Local - Vagrantfile.local

After install GoAnywhere is started as a Daemon service.

At this point GoAnywhere will be running and to use you will need to login to the portal and provide a product key (trial license available)

## Software needed
 * Vagrant
 * Oracle VMWare virtualbox

# Vagrant Forwarded port numbers
```
| Guest Port | Host Port | Service |
| 80         | 8080      | HTTP Server |
| 2221       | 221       | SFTP Server |
| 8001       | 8081      | Admin console https |
```

# Install Script

Vagrantfile uses an install script `post_install.sh` to install basic software (JDK) and begins the GoAnywhere install process - a prompt will take input on install so the string below is used to automate the progression through the prompts.


```
\n\n\n\n\n1\n\n8000\n8001\n1443\n2221\n1990\n2222\n8010\n8009\n8005\n
```

# GoAnywhere Port Numbers

The install / prompt process sets up the following Ports.

```
What port numbers should GoAnywhere MFT use?
Administration Port
[8000]

Secure Administration Port
[8001]

HTTPS Service Port
[1443]

FTP Service Port
[2221]

FTPS Service Port
[990]
1990
SFTP Service Port
[2222]

GoFast Service Port
[8010]

Agents Service Port
[8009]

Shutdown Port
[8005]
```

# Starting up

The install uses a daemon process to startup, on startup you should see a GoAnywhere service.

```
vagrant up
```

## Troubleshooting

Should the service not start up via the daemon:

1) Check software installed / extracted correctly - under /opt/Linoma_Software/GoAnywhere/

2) Manually start and observe outputs
```
/opt/Linoma_Software/GoAnywhere/goanywhere.sh start
```

# Logging in

On your local machine:

https://localhost:8081/goanywhere/

User "administrator" with "goanywhere" as the password
