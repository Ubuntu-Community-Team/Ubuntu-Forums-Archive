---
title: "remote login from Windows VISTA"
date: 2011-03-28
forum: General Help
---

### Post by spindler on 2011-03-28
I need to remotely Ubuntu 10.10 server.   However I want to do it froma Windows XP VISTA or Windows 7 machine.   Ideall I would like to login using http web browser. 
 
The primary reason is because I want to be able to update the server software remotely when required.  Ofcourse it would be nice to see the GUI and be able.10 to perform all functions as if I was sitting at the computer.
 
I heard of webmin.... or webadmin...  However I have not find this software in the Ubuntu Software Centre  and I would like it to be good for Ubuntu 10.10.
 
Any suggestions how I can do this? 
 
 
Thanks,
 
Spindler

---

### Post by blueridgedog on 2011-03-28
Webmin can be installed from the deb package from the site:

[http://www.webmin.com/](http://www.webmin.com/)

Alternatively, you could use VNC or simply secure shell.

---

### Post by newbuntuxx on 2011-03-28
Use ssh.

First, install it on your ubuntu machine:

```
sudo apt-get install openssh-server
```

Then download putty on your windows machine:

[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)

Run it, and in the host name field type your ubuntu ip address. Click on open. It will ask you for your ubuntu user name and then password.

PS. Data transferred via VNC is not encrypted. Therefore, it is not recommended to use it over public networks.

---

### Post by seawolf167 on 2011-03-29
+1 for Webmin

As suggested two other options would be using a vnc-viewer.exe program ([example]("http://www.uvnc.com/download/1055/1055viewer.html")) or use ssh (if you go the ssh route - read up on *screen* it makes life muchhhhh easier)

---

### Post by spindler on 2011-03-29
Using ssh and putty is really easy. Thanks alot. This is great advise. 
 
 
I just have a couple of questions about how to us ssh..... sorry.... newbie stuff.
 
 
1. How do I perform a software update from a shell?.. normally I would use the gui tool "Ubuntu software update".
 
2. How do I restart the computer? What is the command to make the computer shutdown then restart using the shell?
 
3. How do I transfer a file from my laptop to the server using ssh/putty connection? 
 
The reaosn why I ask about the last question is because my router DIR-655 does not like FTP..... I have another forum discussion on this topic. 
 
Thanks
 
Spindler

---

### Post by newbuntuxx on 2011-03-29
> 1. How do I perform a software update from a shell?.. normally I would use the gui tool "Ubuntu software update".

```
sudo apt-get upgrade
```

> 2. How do I restart the computer? What is the command to make the computer shutdown then restart using the shell?

```
sudo reboot now
```

> 3. How do I transfer a file from my laptop to the server using ssh/putty connection? 

On your laptop, download: winscp ([http://winscp.net/download/winscp432setup.exe](http://winscp.net/download/winscp432setup.exe)). This is a gui client which will allow you to transfer files to/from ssh server.

---

### Post by spindler on 2011-03-29
Thanks  :P
 
 
 This solved all of my problems I have been having the last couple of days. :KS
 
 
:popcorn:
 
Spindler

---

### Post by seawolf167 on 2011-03-29
> **spindler said:**
> 3. How do I transfer a file from my laptop to the server using ssh/putty connection? 

The other questions have been addressed - you can do #3 with [putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html") also, just use [this]("http://the.earth.li/%7Esgtatham/putty/latest/x86/pscp.exe") version instead of the "[normal]("http://the.earth.li/%7Esgtatham/putty/latest/x86/putty.exe")" version.

---

