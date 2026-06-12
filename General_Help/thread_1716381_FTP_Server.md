---
title: "FTP Server"
date: 2011-03-28
forum: General Help
---

### Post by ITFS on 2011-03-28
I've set up a FTP server with VSFTP. I have a Comcast business gateway and a static IP. Does anyone know how I can set it up to be accessed from the internet?
Thanks, JT

---

### Post by mendhak on 2011-03-28
Do you have a router (is that your "Comcast business gateway")?  You'll need to go into your router options and allow port forwarding of port 21 to your machine's IP address (on the internal network).

As for connecting to it, you can simply connect by the static IP address (which is external).  Try FileZilla, for example.  Enter the IP address and the port number (or leave it as it is if you didn't change the port number) in the quick connect bar at the top.

Edit: It's 20/21.  I confused it with SSH's 22.

---

### Post by antaios256 on 2011-03-28
for FTP you would want to actually allow port forward for 20 and 21 - (21 being the connection management port and 20 the data port)

---

### Post by ITFS on 2011-03-28
I've forwarded ports 20 and 21 both public and private to the ip for the ftp server. It asks for an application name which cannot be left blank. what do you recommend I put in there?

---

### Post by nice_like_rice on 2011-03-28
The router asks for an application name?

It doesn't matter what you write in there, it's just a tag so you know what it was used for later, just put "ftp" or whatever in :)

---

### Post by newbuntuxx on 2011-03-28
The application name can have whatever you like in it. Just put: vsftp.

Also, are you aware that information transferred over ftp is sent in clear text? So, your username/password/data is vulnerable for sniffing.

PS.
Remember to allow ports 20 and 21 on your ubuntu firewall (ufw or firestarter) if you have them enabled.

---

### Post by ITFS on 2011-03-28
Good to know. But I still cannot connect. I'm using the external IP with the user name and password from a windows system with leechFTP and it says "socket error no connection". I can connect fine using the local ip within the network

---

### Post by newbuntuxx on 2011-03-28
on your ubuntu machine, run:

```
sudo tcpdump port 21 or 20
```

Then try to connect from an external ip to your vsftp server. 

See if the tcpdump shows anything (it should show the ip address that you are trying to connect from), if it does, then the forwarding is done correctly, but you have some other issue.

Can you tell us a bit more about your router? Does it have a stateful inspection firewall built in to it?

---

### Post by ITFS on 2011-03-28
It worked using my phone as a modem and it worked for my wife at home.

Thanks everyone.

---

