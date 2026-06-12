---
title: "Where do I find my server IP address?"
date: 2010-08-06
forum: General Help
---

### Post by frozenfire0808 on 2010-08-06
so i can play my Playstation 3 game Age of Booty online. I'm at my windows xp computer but you can explain directions for ubuntu if its easier

---

### Post by Bachstelze on 2010-08-06
What is "my server"? Where is it located?

---

### Post by frozenfire0808 on 2010-08-06
its on my router im trying to fix the ports so i can play my game since some of the ports are closed apperntly but i cant save it without puting in a sever ip address by default mine says 10.0.0.    but i dont what to put in the last spot

---

### Post by Bachstelze on 2010-08-06
You can get it with

```
ifconfig
```

---

### Post by pipemartinm on 2010-08-06
Not exactly sure what you're trying to do here. What is "my server"?  Where are you trying to connect from and to? For a start though, to display the ip of a linux box just use ifconfig
```

matt@dsk-u104:~$ ifconfig
eth0      Link encap:Ethernet
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0

```If your server is running windows use  ```
ipconfig /all
```

---

### Post by frozenfire0808 on 2010-08-06
that gave me a few ip address which one do i use  the          IP Address   Subnet Mask    Default Gateway  DHCP Server DNS Server  or DNS Servers

---

### Post by pipemartinm on 2010-08-06
> **frozenfire0808 said:**
> that gave me a few ip address which one do i use  the          IP Address   Subnet Mask    Default Gateway  DHCP Server DNS Server  or DNS Servers
Details, dude. What exactly are you trying to do here. The default gateway will be your router if that helps.

---

### Post by frozenfire0808 on 2010-08-06
ok i'll try that

---

### Post by frozenfire0808 on 2010-08-06
that worked except port 3658 it said The specified port(s) are being used by other configurations. Please check your configurations of Remote Management, Port forwarding, Port Triggering, UPnP Port Mapping table, RIP, and Internet connection type    uhh i dont know what to do

---

### Post by frozenfire0808 on 2010-08-06
since this is no longer a server IP address Question I'll start a new thread tommrow with a title of  How to open port 3658?    thanks everyone who helped or at least looked to see if they could help

---

### Post by hawthornso23 on 2010-08-06
Dude - you need to log into your router.

Open firefox and enter  [http://10.0.0.0](http://10.0.0.0)  (substitute the actual IP address of your router - try  also 10.0.0.1 or 10.1.1.1). If you get the right IP address a login creen will pop up. The login name for most routers is `admin', and the password is likely to be either blank or possibly `password'. 

If this doesn't work you might have to google the make of your router to find the correct IP address, login name and password. Once you are logged into your router via the web interface you can look up the IP addresses it has assigned to every device on your local network. You will also find the tools you need to set up port forwarding there.

---

