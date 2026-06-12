---
title: "Access computer through internet"
date: 2009-10-16
forum: General Help
---

### Post by SteveHomoki on 2009-10-16
Hello I'm not very experienced in internet file sharing but I'm working on becoming competent in this area to enhance my computer skills.

I need to set up a way for me to access my files that's either on my usb drive or on my hard drive securely over the internet no matter where I am. (Consider the logmein.com services as _not_ an option, thanks) 

I've read up on remote desktop connections in xp but I'm not being successful in a connection.

I have two options
1. I can try to get my laptop to run ubuntu server 32bit and have my files onto there and then with a wireless connection be able to access my information.

2. I have a spare 2ghz p4 desktop and just connect it to the router as a ubuntu server. With ubuntu server installed, how would I have it set up? Sorry for the general question, I haven't completly experienced Ubuntu as well as other linux distros. I've installed and uninstalled them. I've only tried ubuntu desktop 8.0,suselinux pro 9.0-10.0 and Damn Small Linux to expand my knowledge.


P.S. is there a way I can see the user interface of the desktop if I don't have a spare monitor for it? Perhaps a program that it would just require an internet connection?

---

### Post by Johnny B on 2009-10-16
try ssh and remote desktop, there are many tutorials on the subject

---

### Post by marshmallow1304 on 2009-10-16
Have a look at the [Ubuntu Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html"), with special attention to the page on [OpenSSH]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html").

As for getting a GUI, you can use [X11 forwarding]("http://wiki.linuxquestions.org/wiki/X11_forwarding_with_OpenSSH").

---

### Post by SteveHomoki on 2009-10-16
Thanks, I'll install it to my laptop and see how it goes from there.  Also, any idea for seeing my user interface on the desktop from another system with a monitor? I'd hate to swap vga cords constantly.

---

### Post by MaindotC on 2009-10-16
> **SteveHomoki said:**
> Thanks, I'll install it to my laptop and see how it goes from there.  Also, any idea for seeing my user interface on the desktop from another system with a monitor? I'd hate to swap vga cords constantly.

On the machine you want to view, go to System -> Preferences -> Remote Desktop.  There you will see options for enabling [VNC access](http://en.wikipedia.org/wiki/Virtual_Network_Computing).

---

### Post by SteveHomoki on 2009-10-22
Ok, now I've stumbled upon an issue. I followed the steps for installing it and I didn't come across any issues untill I restarted it. The problem is that all I am getting is a root console command interface(like cmd the best way I can explain it). I was expecting a gui but I only saw a command line. Though I did notice when it was booting up that an "image" was not found.

---

### Post by 3rdalbum on 2009-10-22
Ubuntu Server does not contain a GUI. It is command-line only. For your purposes you should have just installed regular Ubuntu and put server packages onto it.

If you put in a network cable and run the commands:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

it will turn your Ubuntu Server installation into the Ubuntu Desktop so you can have a GUI.

File sharing is a different proposition to just interacting with your desktop over the Internet. For file sharing, you will want to install the Samba package and set that up, and then make sure that your modem/router forwards the Samba ports to your server.

---

