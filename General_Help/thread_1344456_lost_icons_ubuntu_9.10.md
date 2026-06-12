---
title: "lost icons?? ubuntu 9.10"
date: 2009-12-03
forum: General Help
---

### Post by Len Tyree on 2009-12-03
i'am in trouble again...

booted my computer this morning and got 'two' sound icon's, but no connect icon for the internet??

thus i said 'i don't need this' so i clicked on the first one (where the internet icon usualy is) to remove it, via remove from panel.

both of the sound icon's disappeared??

now I am unable to get the sound icon back and load them onto the panel?  got the internet connection back.

so how do I do this, please, a little help.

thank you, len tyree.

---

### Post by NoBugs! on 2009-12-03
The command to start the networkmanager should be "nm-applet".

---

### Post by Len Tyree on 2009-12-03
hi NoBugs, and thanks..
don't know anything about networkmanager.
but tried this...

len@len-desktop:~$ sudo nm-applet
[sudo] password for len: 

** (nm-applet:3658): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

dont understand??

len.

---

### Post by NoBugs! on 2010-01-18
Maybe it's running but not responding? Did you check in System Monitor?

---

### Post by audiomick on 2010-01-18
You don't need to do this,

> **NoBugs! said:**
> The command to start the networkmanager should be "nm-applet".

because, if I understood your first post correctly, you have the internet back.

If you can get into the 'net, the network manager is already running, hence
> Could not acquire the NetworkManagerUserSettings service as it is already taken. Return: 3


Don't know about the sound icon. You should be able to get it back out of the list that you get with a right click on the panel.

---

