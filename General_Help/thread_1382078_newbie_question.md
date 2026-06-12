---
title: "newbie question"
date: 2010-01-15
forum: General Help
---

### Post by sixstringssteve on 2010-01-15
Well, I am a windows convert, so I still speak Microsoft most of the time.  i am trying to learn the Ubuntu way but I am running into some speed bumps.  I have a machine running 9.1 server and I have run into all kinds of issues in the Gnome GUI.  I know all you guys are going to tell me the GUI is for wanna be's, but I don't have the time to submerge myself in a new terminal language 100% of the time, the GUI comes in handy when I am in a pinch.  A huge issue I am having with server, that I do not have with 9.1 desktop, is the constant battle for root authority.  I can easily get root user authority in the terminal but there are times I would like to use the GUI as root.  Is there a way to give myself root authority in Gnome for a session by session basis?  I really would like to do simple things like mount a drive and stuff like that from the GUI.
 
Thanks for putting up with my ignorace, gimme a few months and I'll be helping others.
 
Steve

---

### Post by Portmanteaufu on 2010-01-15
> **sixstringssteve said:**
> Well, I am a windows convert, so I still speak Microsoft most of the time.  i am trying to learn the Ubuntu way but I am running into some speed bumps.  I have a machine running 9.1 server and I have run into all kinds of issues in the Gnome GUI.  I know all you guys are going to tell me the GUI is for wanna be's, but I don't have the time to submerge myself in a new terminal language 100% of the time, the GUI comes in handy when I am in a pinch.  A huge issue I am having with server, that I do not have with 9.1 desktop, is the constant battle for root authority.  I can easily get root user authority in the terminal but there are times I would like to use the GUI as root.  Is there a way to give myself root authority in Gnome for a session by session basis?  I really would like to do simple things like mount a drive and stuff like that from the GUI.
 
Thanks for putting up with my ignorace, gimme a few months and I'll be helping others.
 
Steve

Welcome to the forums, Steve!

While the terminal is awesome and worth learning, I don't think anyone is going to flame you for clicking the mouse. That's what it's there for. :P

It sounds as though you should look into "gksudo". It's a command that will open up whatever graphical thing you're trying to run but with root privileges. 

See [this page]("http://ubuntulinuxhowto.blogspot.com/2006/06/root-access-with-sudo-and-gksudo.html") for an explanation of the gksudo command as well as a how-to illustrating how to create a root user you can log in as if you really need to.

Hope that helps!

---

### Post by sixstringssteve on 2010-01-15
Cool, that works great for the applications.  I put that one on a sticky-note in my office.  There is an issue with Server as it doesn't have a users-admin file.  I didn't realize the vast differences between desktop and server editions.  the gkduso helps with a specific app but not with general maintenece.  for instance...my admin user doesn't have the authority to eject a CD-ROM, yet under root terminal I can eject it.  How do I use gksudo to give me root authority when I am working in on the desktop or in the system files via GUI?
 
Thanks for the help

---

### Post by Portmanteaufu on 2010-01-15
> **sixstringssteve said:**
> ....
How do I use gksudo to give me root authority when I am working in on the desktop or in the system files via GUI?


Hrm -- if I'm understanding you correctly, you'd like to work with the file manager itself as root? If that's the case, you can do that with gksudo too:

```
gksudo nautilus
```

Does that answer your question?

---

### Post by sixstringssteve on 2010-01-15
sweet, thanx man appreciate the help.  i'll be a regualr here I am sure

---

### Post by louieb on 2010-01-15
[forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

Just use sudo or gksudo as needed. 

> ..my admin user doesn't have the authority to eject a CD-ROM, yet under root terminal I can eject it.

Sounds like you did some type of minimal desktop install. Just wondering what parts of gnome you installed.  I would recommend installing meta package ubuntu-desktop  Or heres a really good how to on building a minimal Gnome ["Ubuntu-Desktop-Minimal"  ck post #121 too]("http://www.uluga.ubuntuforums.org/showthread.php?t=1155961") 

> I didn't realize the vast differences between desktop and server editions.

Not much difference - the server kernel is compiled with different options and that about it.

---

### Post by Portmanteaufu on 2010-01-15
> **louieb said:**
> [forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")


Ooo. Did *not* know that was a policy. Thanks for pointing that out. I've come to prefer gksudo and sudo anyway.:P

---

### Post by sixstringssteve on 2010-01-15
I may have installed a minimal desktop, but I didn't intend to.  i noticed right away that the gnome on the server was very different from the desktop edition.  I assume I can reinstall gnome, but can I give it the same version I am used to on my workstation?

---

### Post by sixstringssteve on 2010-01-15
I completely agree with not running a machine in root as standard behavior.  The issue some people run into is that it is a neccesary evil at times.  iwas just looking to do it during cetain sessions that I wanted to use the GUI.

---

