---
title: "dpkg issues"
date: 2009-12-13
forum: General Help
---

### Post by yaodin on 2009-12-13
I tried to access the synaptic package manager today and received an error saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I also on random occasion recieve the follow in error message when trying to open  synaptic package manager.

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."

When I check the system monitor it does not say that any program that could lock dpkg is open (such as apt-get, synaptic, dpackage or aptitude). 

When I try to run 
"sudo dpkg --configure -a" in a terminal it freezes (or sits there longer than I am willing to wait) or on some occasion returns this:

dpkg: status database area is locked by another process

When I run "sudo apt-get update" I receive the following errors

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Have also tried "sudo apt-get -f install" and receive "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

The command "ps ax | grep dpkg" Returns this

 2736 pts/0    S+     0:00 dpkg --configure -a
 2737 pts/0    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/ddclient.postinst configure 
 2744 pts/0    S+     0:00 /bin/sh /var/lib/dpkg/info/ddclient.postinst configure 
 2745 pts/0    S+     0:00 /bin/sh /var/lib/dpkg/info/ddclient.postinst configure 
 3156 pts/1    S+     0:00 grep --color=auto dpkg

...fun...
Thanks for the help in advance.
Austin

Oh, system info: Ubuntu Karmic

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Well most of your errors are because you can't have more than one package manager running at once. IE can't run synaptic while running apt-get... That is why it can't get a lock on /var/run/dpkg/lock... it's already in use. Close out all of your package managers or reboot to ascertain none are running and then run the sudo dpkg --configure -a again.

---

### Post by slakkie on 2009-12-13
> **Sin@Sin-Sacrifice said:**
> Well most of your errors are because you can't have more than one package manager running at once. IE can't run synaptic while running apt-get... That is why it can't get a lock on /var/run/dpkg/lock... it's already in use. Close out all of your package managers or reboot to ascertain none are running and then run the sudo dpkg --configure -a again.

No need to reboot, just kill the hanging processes

kill 2736 2737 2744 2745 3156

Or kill -9 if they stay alive after the normal kill.

Then rerun your actions.

---

### Post by yaodin on 2009-12-13
Awesome it worked. For reference all I did was ps ax | grep dpkg then sudo kill -9 XXXX the 3 relevant processes. 
Thanks 
Austin

Edit: Sorry I spoke to soon. I can kill the processes so that a new running of ps ax | grep dpkg only brings it's self up but I still have an issue with dpkg. When I run sudo dpkg --configure -a It still just sits there. Also when I go into synaptic and try to install a program in the terminal the install freezes at "setting up ddclient..."

---

### Post by yaodin on 2009-12-13
So I let "sudo dpkg --configure -a" run for about a hour and a half and it returned an error contained in an in-terminal gui. It said some dns service was misconfigured or had invalid user name and password. To fix this run "dpkg -reconfigure ddclient" this command returned "dpkg: conflicting actions -e (--control) and -r (--remove)".

This suddenly made me think of a type of lojack system i was trying to set up a little while ago following [this tut]("http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer"). So to resolve the issues I may have caused I upgraded ddclient and tested by installing a random game from synaptic and I am golden.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
> **yaodin said:**
> So I let "sudo dpkg --configure -a" run for about a hour and a half and it returned an error contained in an in-terminal gui. It said some dns service was misconfigured or had invalid user name and password. To fix this run "dpkg -reconfigure ddclient" this command returned "dpkg: conflicting actions -e (--control) and -r (--remove)".

This suddenly made me think of a type of lojack system i was trying to set up a little while ago following [this tut]("http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer"). So to resolve the issues I may have caused I upgraded ddclient and tested by installing a random game from synaptic and I am golden.

Thats ```
sudo dpkg --reconfigure ddclient
``` You missed a dash there.

---

