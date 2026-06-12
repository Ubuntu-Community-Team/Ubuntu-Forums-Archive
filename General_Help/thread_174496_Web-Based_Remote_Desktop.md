---
title: "Web-Based Remote Desktop"
date: 2006-05-11
forum: General Help
---

### Post by jflash on 2006-05-11
I am wanting to find a good program that will let me to my Ubuntu box from over the internet and control it (preferably including uploading files from anywhere on my drive, etc). My only problem is that I need for a)the program to be compatible with Windows and b)for it to be web based. If anyone knows of such a program, please let me know. Thanks!

---

### Post by nanotube on 2006-05-12
look into [https://ubuntucenter.bountysource.com/wiki](https://ubuntucenter.bountysource.com/wiki)
it is a web-based control thing for ubuntu.
haven't tried it myself, and it is beta-quality software, but looks promising.

---

### Post by simonn on 2006-05-12
[http://www.webmin.com](http://www.webmin.com)

I have been using it for years. Works very well even through even a fairly restrictive firewall - I can only do https on port 443, no telnet or ssh from work. Tunnelling is naughty too.

If you are going to be onpening it up to the world, run it using https, not vanilla http.

Also, install the minimal system to /opt and add the modules you need. I have found that I tend to use only file manager, shell and shell in a box. Shell in a box is a little temperamental - disconnects for no reason every now and then, but you wil not be able to run anything interactively if you do not use it.

---

### Post by jflash on 2006-05-12
I already use Ubuntu Center and love it, but I'll definitely look into Webmin.

However, I'm looking more for something that will allow me to work on my computer by letting me work with the Ubuntu interface (basically a remote control app is what I'm needing). As i said, it nees to be web-based (which rules out the vncviewer program discussed in ubuntuguide.org) and it needs to be compatible with Windows.

---

### Post by jflash on 2006-05-13
I have since started using Webmin, and am very impressed, but I would still like a remote desktop tool.

---

### Post by souki on 2006-05-13
[quote=jflash]I have since started using Webmin, and am very impressed, but I would still like a remote desktop tool.[/quote] 
do you mean "you want an applet inside your browser to display a remote desktop" ?
there is a java applet for vnc

---

### Post by rvergara on 2006-05-13
[QUOTE=jflash]I already use Ubuntu Center and love it, but I'll definitely look into Webmin.

However, I'm looking more for something that will allow me to work on my computer by letting me work with the Ubuntu interface (basically a remote control app is what I'm needing). As i said, it nees to be web-based (which rules out the vncviewer program discussed in ubuntuguide.org) and it needs to be compatible with Windows.[/QUOTE]


Try freenx. There is a No Machine client for windows and it works spotlessly. It can be run even in dial up connections so you should be able to work remotely regarless of the quality of your Internet connection.

Regards

Ramiro

---

### Post by jflash on 2006-05-13
It looks good, but when I try to install the .deb file I downloaded, it tells me it needs the packages nxagent and expect. I have tried to get both by using apt-get and Synaptic, but to no avail. I'll keep looking, but please let me know if you know where I can find them.

EDIT: I did end up finding the required packages and installing them, bu I now need to know how to configure this so I can get it to work with Apache and let me access my computer over the internet.

EDIT2: Souki, where can I find that? That is what I want.

---

### Post by souki on 2006-05-14
there is a java applet viewer for both solutions (freenx and vnc)
just use the search fonction

here, a thread on vnc
[http://ubuntuforums.org/showthread.php?t=107503&highlight=vnc-java](http://ubuntuforums.org/showthread.php?t=107503&highlight=vnc-java)

and a thread on freenx
[http://ubuntuforums.org/showthread.php?t=174243&highlight=freenx+java](http://ubuntuforums.org/showthread.php?t=174243&highlight=freenx+java)

---

### Post by jflash on 2006-05-14
Ah, thanks. It works now. Thank you so much!

---

