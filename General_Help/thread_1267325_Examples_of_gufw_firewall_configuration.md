---
title: "Examples of gufw firewall configuration"
date: 2009-09-15
forum: General Help
---

### Post by sopadeajo on 2009-09-15
It would be nice if experienced people post here their gufw firewall configuration (or just an example of it)  explaining why they did such a configuration and how it helps their computer to be safe. This would help beginners like me to learn more about network protection.
Isn't it a good idea?
By the way there is no help file at all with gufw 0.20.7. Why is it?

---

### Post by mikewhatever on 2009-09-15
I think it's a bad idea, since every one's setup is a bit different.
The truth is, most users don't need a firewall, and only want it because they are used to running one on Windows. If you need help using the GUI, check out the guide. [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by jmszr on 2009-09-15
sopadeajo,

This may be of some interest to you, it includes a section on the Ubuntu firewall: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by sopadeajo on 2009-09-15
mikewhatever, i understand your point of view, you want to defend Linux against exterior agresions, but your defense is  a defense of SECURITY through OBSCURITY. My defense of open and free software is a defense of SECURITY through KNOWLEDGE.
I waqnt simply people to know more about networks and then decide if using a firewall (with GUI or not) or not.
So you should add a help file to gufw and i insist that a kind of tutorial (a kind of an example) on how to use gufw when needed would increase knowledge and thus security.Do not be obscur mister mikewhatever

---

### Post by sopadeajo on 2009-09-15
Reading the bugs page of the writer of gufw i learned that the application could not load at Ubuntu start because there was not the folder autostart in home/user/.config
once this done gufw loads with Ubuntu.
It is very probable that the firewall will not be needed on every session, but it's to you to uncheck it .

---

### Post by winotree on 2009-09-15
There may not be a manual, as such.  :?  This is from the home page [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

**gufw** [http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html](http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html) as you know, is the GUI for the terminal program **ufw** [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html) which makes sense of the default **iptables** [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) and although I didn't read all of [http://www.dedoimedo.com/computers/gufw.html](http://www.dedoimedo.com/computers/gufw.html) I've *never been disappointed by anything* from this blog.  Hope something here catches your interest.  ;)

---

