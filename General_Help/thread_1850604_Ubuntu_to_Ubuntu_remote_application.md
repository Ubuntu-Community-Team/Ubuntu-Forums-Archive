---
title: "Ubuntu to Ubuntu remote application"
date: 2011-09-26
forum: General Help
---

### Post by cswcu48 on 2011-09-26
Hey guys,

I would like to use my 11.04 ubuntu desktop as my main base of operations.  I have a laptop that I am running 10.10 on.  Is there any application that is free where I can remote into my desktop from my laptop as long as I have an internet connection.  Does anyone know of anything?  Sorry for the noob question...

---

### Post by jonnyboysmithy on 2011-09-26
Yup there is,
vinagre is what your after 
```
sudo apt-get install vinagre
```

Edit:I haven't used it myself but it came with 11.10 so maybe try that?

---

### Post by cswcu48 on 2011-09-26
Thank you for the reply.  How exactly does this work.  can it connect from gnome 10.10 to a unity 11.03 desktop?

---

### Post by sammiev on 2011-09-26
I know little about vinagre and it might be safe, but something like openssh is a must over the internet. :) Try a search on openssh and read on. :popcorn:

---

### Post by cswcu48 on 2011-09-27
Perhaps I did not clarify.  Is there anything that can be used to remote into my linux machine to view is desktop and sue it's applications just like you can sue remote desktop to remote into windows machines and use whatever is installed on them with ease.
 
Does anyone know of any programs that allow a linux machien to remote into a linux machine without having to go through the process of adding it to the domain or anything like that?

---

### Post by seawolf167 on 2011-09-27
Use [SSH]("https://help.ubuntu.com/community/SSH") + [screen]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/") for all your remote needs. If for some reason you need to run X applications, use X [Forwarding]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") over SSH (the "-X" switch).

Additionally, you can use [VNC]("https://help.ubuntu.com/community/VNC"), and viewers like the [UltraVNC]("http://www.uvnc.com/") Viewer.

---

### Post by matt_symes on 2011-09-27
Hi

Teamviewer ?

> Remote administration of unattended servers and such like.

[http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx)

A VNC variant. Make sure it is a secure one if you go down this route.

Kind regards

---

