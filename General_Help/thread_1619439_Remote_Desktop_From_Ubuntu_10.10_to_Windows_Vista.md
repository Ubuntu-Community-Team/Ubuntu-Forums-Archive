---
title: "Remote Desktop From Ubuntu 10.10 to Windows Vista"
date: 2010-11-11
forum: General Help
---

### Post by rujol on 2010-11-11
Hello, i've been trying to connect to my stationary computer from my laptop.
My stationary computer uses Windows Vista 32 and my laptop uses Ubuntu 10.10.
I'm trying to connect to my vista computer without luck, i have installed RealVNC on my vista, opened port 5900, 5800 and 3389 on my router.
My laptop is Wireless and my stationary is on cable.
Tried using Terminal Server Client without luck, i get this message:


```
Connected to RFB server,using protocol version 3.8
Performing standard VNC authentication
Authentication Successful
vncviewer:VNC server closed connection
```
 
I've tried adding my laptop static ip on RealVNC in the config.
I have shut down windows firewall, I'm running no security, i have opened for Remote connection by right clicking My computer and in network connection.
Im Running a Linksys WRT54GL with Firmware: DD-WRT v24-sp2 (10/10/09) std 

any idea of what im doing wrong? :(

---

### Post by lmarmisa on 2010-11-11
If your Vista OS is Pro edition, the Remote Desktop function would be supported and you could use the Applications -> Internet -> Terminal Server Client (RDP protocol) for the remote access to your Vista system. Home Editions of Vista do not provide the Remote Desktop function.

I am not an expert with VNC but I believe that you should try to use the Application -> Internet -> Desktop Viewer and not the Terminal Server Client.

An interesting alternative that I recomment is [TeamViewer]("http://www.teamviewer.com").

---

### Post by rujol on 2010-11-11
> **lmarmisa said:**
>  Home Editions of Vista do not provide the Remote Desktop function. 

Im using Home Edition at the moment yes.

> **lmarmisa said:**
> I am not an expert with VNC but I believe that you should try to use the Application -> Internet -> Desktop Viewer and not the Terminal Server Client.

I tried using that aswell. Get connection Closed after i type my password.

I will try and use TeamViewer, will report on how it goes

---

### Post by ki4jgt on 2010-11-11
Try TeamViewer. It works quite well for desktop sharing and file sharing.

---

### Post by lmarmisa on 2010-11-11
I use [TightVNC ]("http://www.tightvnc.com/")as VNC client in Windows XP Pro and it works great. I think that it can be configured as server as well.

TightVNC could be an alternative to RealVNC.

---

### Post by rujol on 2010-11-11
I thank you all from the bottom of my hearth, and i apologise for making a stupid port, TeamViewer was a no go for me but TightVNC works great, thank you all for your help :D

---

