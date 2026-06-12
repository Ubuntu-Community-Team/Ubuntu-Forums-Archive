---
title: "Click on a link in chrome, Ubuntu make a logoff"
date: 2011-06-01
forum: General Help
---

### Post by Melotten on 2011-06-01
Hi guys,
is few days that randomly, clicking on a link in chrome the system make a logoff, closing all the windOWS I had opened.

never happened to me something like that, do you have any idea what can happened?

any good source? any place where I can get help?

thanks!

Ubuntu Natty in Gnome.. sorry for unity but I will wait better time. :)


thanks a lot guys :)

---

### Post by TheNosh on 2011-06-01
Sounds like X crashed.

---

### Post by Melotten on 2011-06-09
there is any way to reinstall it or to verify what's happen in a log?

---

### Post by Melotten on 2011-06-09
my system is not stable anymore, all the software are closed and nothing is saved. :(

---

### Post by TheNosh on 2011-06-09
> **Melotten said:**
> my system is not stable anymore, all the software are closed and nothing is saved. :(

What do you mean specifically by "not stable"? Also, which software has closed, and what wasn't saved?

---

### Post by Melotten on 2011-06-11
for not stable I mean that if I'm surfing or I move some file or wherever, my system show for a millisecond a black window and after bring me to the login screen.

none of the software I had open has been saved, is like to restart a completely new session.

This start to be annoying, to be honest I don't really know where to look for a solution.

starting from the point that X crash, there is any log to check if this option is the real one.

is it possible to reinstall Gnome in some way?

thanks a lot for your help guys, there is something something to lean here :)

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Melotten said:**
> for not stable I mean that if I'm surfing or I move some file or wherever, my system show for a millisecond a black window and after bring me to the login screen.

none of the software I had open has been saved, is like to restart a completely new session.

This start to be annoying, to be honest I don't really know where to look for a solution.

starting from the point that X crash, there is any log to check if this option is the real one.

is it possible to reinstall Gnome in some way?

thanks a lot for your help guys, there is something something to lean here :)

That sounds nasty. I would try a live stick of Ubuntu 10.10 from a flash drive, leave it booted overnight and check your logs in the morning. You could have bad hardware, so that's why I say that. Run Disk Utility and find out what it says pronto.

---

### Post by teachop on 2011-06-11
This happens to my computer with 11.04 Unity as well.  For me it is mostly in firefox, but sometimes it happens elsewhere.  It is a horrible horrible bug, because everything is lost.  Here is a thread that is similar:
[http://ubuntuforums.org/showthread.php?t=1759011]("http://ubuntuforums.org/showthread.php?t=1759011")

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **teachop said:**
> This happens to my computer with 11.04 Unity as well.  For me it is mostly in firefox, but sometimes it happens elsewhere.  It is a horrible horrible bug, because everything is lost.  Here is a thread that is similar:
[http://ubuntuforums.org/showthread.php?t=1759011](http://ubuntuforums.org/showthread.php?t=1759011)

I quit using 11.04 and installed a fresh copy of 10.10..  Everything works great now.

Try this:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Melotten on 2011-06-12
I will have a look on the thread, do you know if a ticket has been raised for this with canonical?

I think the quality of this release is horrible, I would like to know if someone of the guys actually have a look on this errors.
Never had such problems in the past..

So sad.

BTW, any way to unistall gnome and to reinstall it without to mess up things?

---

### Post by Rifester on 2011-06-12
This is a bug, several reports are filed on Launchpad.   You should go there and mark the bug as affecting you.    I added Xubuntu-Desktop and now have no crashes (while running Xubuntu).  

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490)

---

### Post by ssreddy555 on 2011-06-12
Does this happen even with classical interface?

---

### Post by Rifester on 2011-06-12
Yes, many people have reported it in Unity and classical interface.    I don't have this issue at all when running in Xubuntu for some reason, so I am sticking with it until this bug gets fixed.

---

