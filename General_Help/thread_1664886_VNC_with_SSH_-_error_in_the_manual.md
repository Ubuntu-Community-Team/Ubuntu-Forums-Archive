---
title: "VNC with SSH - error in the manual?"
date: 2011-01-11
forum: General Help
---

### Post by nrabett on 2011-01-11
The otherwise very good manual page [https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC") explains how to use create a ssh tunnel for vnc. I have fought with this explanation for some days, and hopeless trial and error finally worked. Here is the explanation

[SIZE="1"]Each time you want to connect to your PC, follow these steps:

Find your PC's public name or IP address. Unless your PC has been assigned a memorable name, the easiest way to do this is to go to whatismyip.com from your PC. You can assign your PC a name by getting one from a dynamic DNS provider
Start the SSH client on the computer you'll log in from.
Tell the SSH client to use local port-forwarding to connect port 5,900 on your desktop to port 5,900 on localhost.
Via the SSH client, run the command x11vnc -safer -localhost -nopw -once -display :0 on the computer whose desktop you will view.[/SIZE]

I have tried this many times using ConnectBot and Android VNC viewer from a phone. I finally found a solution on this page

[http://code.google.com/p/connectbot/issues/detail?id=329]("http://code.google.com/p/connectbot/issues/detail?id=329")

- where someone suggests to create a local port forward. The person who asks in this thread, has apparently read the same manual as I. The suggestion works, but I am not entirely certain that I have created a secure connection by "locally" forwarding port 5900 on the phone to localhost:5900. Can someone confirm this?

Am I correct in assuming that the line "Tell the SSH client to use local port-forwarding to connect port 5,900 on your desktop to port 5,900 on localhost." in the explanation should read "on your remote laptop"?

---

### Post by nrabett on 2011-01-12
An update: The method described in the manual actually worked quite well when trying to connect via SSH and VNC to a Windows 7 64bit machine with TightVNC server and MobaSSH server. In this case, it turned out to be necessary to use local port forwarding with ConnectBot, from port 5900 to the remote host, on my LAN 10.0.0.101:5900 as opposed to localhost:5900 in the previous post. (The client address was 10.0.10.100.)

This is a difference between Ubuntu and Windows that I do not understand. Or is the difference really between the different SSH servers (MobaSSH and Ubuntu standard)?

I am also not sure if the connection I have made - from port 5900 to 10.0.0.101:5900 is actually a SSH tunnel.

(So...the manual is apparently correct when one assumes that the server runs on a Windows PC... but why should we assume this?)

---

