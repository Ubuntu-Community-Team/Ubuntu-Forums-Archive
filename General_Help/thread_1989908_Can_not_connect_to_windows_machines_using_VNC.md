---
title: "Can not connect to windows machines using VNC"
date: 2012-05-29
forum: General Help
---

### Post by Inderpreet Singh on 2012-05-29
Hi,

I am using ubuntu server 11.10 ( I have Installed Ubuntu-desktop environment on in)  , We have many windows machines in our network each windows machine have Real VNC server installed on them. I am able to connect VNC from windows to windows but not able to connect VNC from ubuntu server to Windows machine. I am using default VNC from terminal. Whenever I try to connect any vnc machine it gives me error--

CConn:       connected to host 172.x.x.x port 5900
 CConnection: Server supports RFB protocol version 4.1
 CConnection: Using RFB protocol version 3.8
 CConnection: No matching security types
 main:        No matching security types

Please Provide me the solution.

---

### Post by albandy on 2012-05-29
Install vinagre:
sudo apt-get install vinagre

---

### Post by Inderpreet Singh on 2012-05-29
Its saying 

vinagre is already the newest version installed

---

### Post by albandy on 2012-05-29
ok. Open vinagre and try to connect.

---

### Post by Inderpreet Singh on 2012-05-29
> **albandy said:**
> ok. Open vinagre and try to connect.
vinagre is also giving error while connecting VNC,however it is able to connect Rdesktop

---

### Post by albandy on 2012-05-29
Try with this one:
```

sudo apt-get install xtightvncviewer

then
xtightvncviewer host:port

usually:
xtightvncviewer 192.168.1.100:5900

```

---

### Post by jim_deadlock on 2012-05-29
Have you tried [Teamviewer]("http://www.teamviewer.com/") - it "just works" and is cross platform.

---

### Post by Inderpreet Singh on 2012-05-31
> **jim_deadlock said:**
> Have you tried [Teamviewer]("http://www.teamviewer.com/") - it "just works" and is cross platform.
hey, jim i know about teamviewer and i use this some time but for local network i always prefer VNC , but its giving me problem on ubuntu

---

### Post by Inderpreet Singh on 2012-05-31
> **albandy said:**
> Try with this one:
```

sudo apt-get install xtightvncviewer

then
xtightvncviewer host:port

usually:
xtightvncviewer 192.168.1.100:5900

```

I have installed xtightvncviewer but when I tried to connect to a vnc machine its giving me error 
Connected to RFB server, using protocol version 3.3
No configured security type is supported by 3.3 viewer
so what can be the solution??

---

### Post by synapsys on 2012-05-31
From the error message you are getting, it looks like you are using RFB version 3.8, but the "server" (VNC server your Windows box) only supports 4.1. It seems that there is an xvncviewer package that uses 4.1 in the Ubuntu Universe repositories. 

[http://pkgs.org/ubuntu-11.04/ubuntu-universe-i386/xvnc4viewer_4.1.1+xorg4.3.0-37ubuntu2_i386.deb.html](http://pkgs.org/ubuntu-11.04/ubuntu-universe-i386/xvnc4viewer_4.1.1+xorg4.3.0-37ubuntu2_i386.deb.html)

If you are just going across the LAN and can connect via RDP, just use that. It's natively supported in Windows and works quite well.

---

### Post by Inderpreet Singh on 2012-05-31
still facing problem....
:(

---

### Post by Inderpreet Singh on 2012-05-31
I am using[B] 
VNC server enterprise edition E4.5.1[/B] on windows So which VNC utility can work on ubuntu to connect with windows machine????

---

### Post by albandy on 2012-05-31
Yo can download vnc enterprise edition for linux from realvnc.

So go to downloads and select the apropiate for your os architecture:

If you've installed Ubuntu 64 bit download this one: VNC Enterprise Edition for Linux (x64)
else if you've installed Ubuntu 32 bit download this one: VNC Enterprise Edition for Linux (x86)

I recomend you to download the gzipped tarfile.

Then extract the contents to your desktop, open the folder and double click in vncviewer.

---

### Post by Inderpreet Singh on 2012-05-31
> **albandy said:**
> Yo can download vnc enterprise edition for linux from realvnc.

So go to downloads and select the apropiate for your os architecture:

If you've installed Ubuntu 64 bit download this one: VNC Enterprise Edition for Linux (x64)
else if you've installed Ubuntu 32 bit download this one: VNC Enterprise Edition for Linux (x86)

I recomend you to download the gzipped tarfile.

Then extract the contents to your desktop, open the folder and double click in vncviewer.

Yes, [albandy]("http://ubuntuforums.org/member.php?u=715896") this worked for me. Thank you so much:)

---

### Post by uzumakifahim on 2013-03-26
I've downloaded that .tar.gz from realvnc website, extract that folder on my desktop. Give permissions "Allow executing files as programs" and then double click on the *vncviewer*, but a window pops up and saying that

[B]Could not display "/home/fahim/Desktop/vnc-4_1_3-x86_linux/vncviewer".
There is no application installed for executable files.
Do you want to search for an application to open this file?
[/B]
When I click Yes. Then it searched for suitable programs to open the file. Then it shows:

[B]Install software to open files?
nemo requires to install software to open files of the following file type: executable
executable is not supported.[/B]

I don't understand why this is happening. Please help anyone.

---

