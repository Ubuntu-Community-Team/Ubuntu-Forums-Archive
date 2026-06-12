---
title: "Building A Headless Ubuntu Server"
date: 2006-03-31
forum: General Help
---

### Post by acascianelli on 2006-03-31
I recently upgraded the harddrive on my server and I thought it would be a perfect time to migrate it from Windows 2003 over to Linux.

I would like to run the server installation of Ubuntu on it but I can settle with with regular Gnome install if need be.

Like I said in the title, this system will be headless.  No keyboard, mouse, monitor.  I will need to be able to log in to it and perform administration from both a Windows XP and another Ubuntu Linux machine.  I was originally going to just use XDMCP to get a remote desktop to the server but I can't find a way to connect to it using XDMCP from Windows.  Then I was going to use VNC, but after searching on these forums for a while I cannot find any way to get XVNC running from the login screen.

So basically I'm asking if anybody knows how to configure VNC so that it will start with X and allow me to connect from a login screen.

---

### Post by Zelut on 2006-03-31
Well what is the end-use of your server going to be?  I have two headless servers at my house (apache, mysql, email, etc, etc) and I do all of my access via ssh.  None of them have GUI installed as thats just a waste of HDD space & resources if you ask me.

---

### Post by acascianelli on 2006-03-31
I'll be using it as a file server and a system I can do lengthy downloads from.

---

### Post by acascianelli on 2006-03-31
Nevermind...

[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

That thread pretty much explained what I want to do and I got it working.  I guess I didn't look hard enough.

---

### Post by trent dillman on 2006-03-31
acascianelli: love the avatar :-D

---

