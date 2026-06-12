---
title: "Panel gone after uninstalling evolution mail"
date: 2009-08-19
forum: General Help
---

### Post by Spyker on 2009-08-19
Hi, so my panel dissappeared but i got it back with the help of this forum.

i used
alt+ctr+F1 to get into terminal(in recovery more)

sudo apt-get install gnome-panel

then restarted my machine

at this point i got a whole bunch of error messages telling me that among other my trashapplet could not be found. i went to synaptic to get it and then i found out that i didnt have internet connectivity while my vista machine next to my ubuntu machine does.

so i checked my settings on ubuntu and they are all correct and still no luck.

so anyway, my question is...is there a known problem of this kind where doing updates and removing evolution causes loss of connection?

and

does anyone have a list of all the ifconfig commands?

Thank you

PS, i'm new to ubuntu 8.4, only started using it last week. SAtanic edition FTW.

---

### Post by mcduck on 2009-08-19
You probably removed some of the Evolution libraries as well.

The thing is that many other components in Gnome desktop depend on those, as quite many programs have the ability to integrate with Evolution. Including some gnome-panel's applets, like the clock/calendar applet.

So, removing those packages broke gnome-panel, and the Network Manager can't run without a panel that provides a notification area for it to place it's icon into.

You'll probably have to tell a bit more details about how you are connecting to Internet for anybody to be able to give you commands to do it from CLI.. But once you get connected again, I recommend installing the "ubuntu-desktop"-metapackage to bring back Evolution and all the important components you are now missing. After that you may try removing Evolution again, but be more careful this time when removing evolution's library packages..

Assuming you are using wired connection, and your network card is eth0, running "sudo ifup eth0" should get you connected.

---

### Post by HermanAB on 2009-08-19
Hmm, trying to unscramble an egg is seldom successful.  If you want to experiment, create a VM on Virtualbox or VMware and play with that.  On your host system, you need to be careful with what you do.

---

### Post by Spyker on 2009-08-21
Yes i connect via a wired connection.
 
and yes, my clock and date on the panel are some of the things that went missing. also my trash bin.
 
thanks for the advice. i'll try those later today.:)

---

