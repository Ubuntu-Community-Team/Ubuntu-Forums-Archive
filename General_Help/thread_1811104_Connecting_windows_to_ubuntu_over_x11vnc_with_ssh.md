---
title: "Connecting windows to ubuntu over x11vnc with ssh"
date: 2011-07-24
forum: General Help
---

### Post by duindain on 2011-07-24
Hi everyone,
Im trying to get vnc working over ssh between my windows pc and ubuntu server 11.04 natty over the internet
I have setup everything and got it all running automatically at boot on ubuntu

From within the local network i can use ssvnc and connect from a 2003 server to the ubuntu machine fine

Remotely I can connect and verify password over ssh but after that it tries to start tightvnc and fails

The issues seem to be on the windows side establishing the local connection to the tunnel or something I'm not a guru and I apologize if this is a windows issue but i think its likely that its a networking problem i need to forward or open a port somewhere but i cant find any easy to understand instructions so far in getting this running

This is the output in the putty terminal after running ssvnc slightly modified ive taken out my real username and server address
I use user@server:0 as the arguments for ssvnc

```

Looking up host "server"
Connecting to server-ip port 22
Server version: SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
We claim version: SSH-2.0-PuTTY_Release_0.60
Using SSH protocol version 2
Doing Diffie-Hellman group exchange
Doing Diffie-Hellman key exchange with hash SHA-256
Host key fingerprint is:
ssh-rsa 2048 key
Initialised AES-256 SDCTR client->server encryption
Initialised HMAC-SHA1 client->server MAC algorithm
Initialised AES-256 SDCTR server->client encryption
Initialised HMAC-SHA1 server->client MAC algorithm
Using username "user".
user@server's password:
Sent password
Access granted
Opened channel for session
Local port 5930 forwarding to 127.0.0.1:5900
Allocated pty (ospeed 38400bps, ispeed 38400bps)
Started a shell/command

SSH connected OK.
If this state is not autodetected,
Go Click the Success button.
Opening forwarded connection to 127.0.0.1:5900
Forwarded connection refused by server: Connect failed [Connection refused]

```I have ports 5900-5905 and 20-25 allowed through the firewall on the ubuntu server also 443 and these are all forwarded for the router at this location as well

No ports are explicitly forwarded on the windows machine yet

Ive tried this remotely using a win xp machine and win 7 both fail at the same point

Does anyone have any ideas why the connection fails at the point of using the tunnel? is it a problem on the ubuntu or windows side?

Thanks for taking a look at my issue
Duindain

---

### Post by duindain on 2011-07-28
Noones using ssvnc to x11vnc using ssh and had these issues?

---

### Post by whitethorn on 2011-07-28
can you post output for a working connecting from within your network. At the moment looks like your server is refusing the connection.

---

