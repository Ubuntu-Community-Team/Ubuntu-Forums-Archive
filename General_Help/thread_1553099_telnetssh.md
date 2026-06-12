---
title: "telnet/ssh"
date: 2010-08-14
forum: General Help
---

### Post by Random_Net on 2010-08-14
Hi,

I've two machines one with windows 7 and other with ubuntu10.04 ( now replaced it with mint ) . I was able to successfully connect them ( I was able to ping one from the other machine ). However, when I tried to open a telnet or ssh connection from windows, there was no response from mint 8. On Mint, if I try 

```
telnet localhost 
```or
```
ssh localhost
```I get:

```
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

``````
ssh: connect to host localhost port 22: Connection refused
```Is this a generic problem or could it be specific to the os?

Edit: solved , I hadn't installed the telnet/ssh servers

---

