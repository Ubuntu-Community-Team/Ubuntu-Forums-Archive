---
title: "Personal file sharing in Ubuntu?"
date: 2011-09-01
forum: General Help
---

### Post by cptrohn on 2011-09-01
OK, I have Samba running on both my desktop and my laptop both running ubuntu 11.04...  With the laptop I was sharing files with windows computers all day today.  Now when I try to use Samba to share files between my ubuntu machines I get an error saying that my desktop can't mount my laptop through my wireless network?  

So I went to the power button > systems > personal file sharing  to see if I could just share through ubuntu's default personal file sharing protocol there but I get an error message on that window when it opens up saying that```
this feature cannot be enabled because the required packages are not installed on your system
```... So which packages do I need installed on my machines to be able to perform file sharing that way, since I can't seem to be able to do so through samba?  Is samba just for windows and linux shares? or am I missing something important here?

I'm trying to share through a wireless network, does this make a difference in samba?

---

### Post by nothingspecial on 2011-09-01
Samba is for windows.

Use ssh to access your files Ubuntu <>  Ubuntu

Install openssh-server

At an empty desktop or a file browser window, click file > connect to server.

Choose ssh and fill in the blanks (don't worry about the port)

---

### Post by cptrohn on 2011-09-01
Ok thanks, so with ssh do I need to set anything up in the personal file sharing package in the systems menu that I found?

---

### Post by michaelb28 on 2011-09-01
I'd recommend NFS for Linux shares over a LAN. It's native to Linux and according to speed tests others have done, faster than Samba or SSH.

---

### Post by michaelb28 on 2011-09-03
Hi,

If you want to use Samba to share files on Linux it is fine. You can either share files on your Ubuntu computers with Samba as a server, or access those files with Samba as a client.  There is a guide to Samba client setup on this page:
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

You may want to see if you have the package smbfs installed. Or it might be nautilus-share that is giving you the missing package error.

Maybe someone else can give you specific direction here on how to set this up. My primary Linux computer is a server that doesn't have a graphical desktop installed, so I'm not familiar with the feature you are referring to. I might be able to try it out on another computer later if I get time though.

---

### Post by Morbius1 on 2011-09-03
[1] Personal File Sharing is not Samba.

It sets up a little baby apache file server and announces it's only share ( your Public folder ) to the rest of the lan using avahi. It barely works between Linux boxes and from what I can tell not at all between Windows and Linux. The only reason it's in the menu is because it comes with a package that enables bluetooth.

[COLOR=Blue]EDIT: Sorry, should have told you how to enable Personal File Sharing so you can decide for yourself it it meets your needs.[/COLOR]

You need to install the following packages:
```
sudo apt-get install apache2.2-bin
sudo apt-get install libapache2-mod-dnssd

```
And remember it only shares one folder: /home/your-user-name/Public.

[2] If you're still interested in sharing a folder using Samba do it the easy way:

Make believe you are sitting in front of a WinXP machine
Open your file manager ( Nautilus ) > right click a folder you own > Select "Sharing Options > Check all the boxes.

If it's missing any packages it will install them for you - all you have to do is say OK.

---

