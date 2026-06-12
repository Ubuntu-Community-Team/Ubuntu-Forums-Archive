---
title: "SMB slow over SSH"
date: 2011-09-12
forum: General Help
---

### Post by Caesius on 2011-09-12
I have the following situation:

A - Ubuntu Server 11.04 running Samba and SSH server
B - Windows 7 SP1 client

I can successfully make a Samba connection through an SSH tunnel from over the internet B to A. I used _[this]("http://www.blisstonia.com/eolson/notes/smboverssh.php")_ method using a microsoft loopback device.

The problem is, the transfer speed is way too low. It averages at 150 KB/s. Other connections, like NNTP, usually run at 1,5 MB/s through the tunnel. As far as I know SMB only encrypts the handshake, so I don't think it's due to the overhead of the connection.

What is causing this low transfer speed? The up/download speed of both connections sufficient. I also checked the CPU usage, and that doesn't seem to be the problem as well.

---

