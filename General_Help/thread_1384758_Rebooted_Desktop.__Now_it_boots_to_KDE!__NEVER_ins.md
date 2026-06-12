---
title: "Rebooted Desktop.  Now it boots to KDE?!  NEVER installed kde!!!!"
date: 2010-01-18
forum: General Help
---

### Post by kireol on 2010-01-18
wow, so i'm running karmic koala.  My desktop is a fresh install.  it sits behind a router.  I'm the only user.


I was installing nautalus-image-convert and tried a /etc/init.d/gdm restart and that did restart to gnome, but naut didnt have the resize options.

So I did a sudo reboot


now I'm in KDE.


I've NEVER installed kde.  I hate kde.  and want gnome back.


Please help :)


#1: how/best way to switch back to gnome.

#2: How to find out wh this happened.

---

### Post by kireol on 2010-01-18
BTW: I"m assuming it's KDE.


The background is blue with bubbles?  and small K with a gear is in the lower left hand window and works as an application launcher/logout.

---

### Post by Ahriman on 2010-01-18
I've done this myself when I started out with Ubuntu. Accidentally installed kubuntu-desktop. :(
1. When you go to log on (either via gdm or kdm), there should be an option to choose Gnome, KDE (and their various failsafes) or terminal. Choose Gnome.
2. not 100% sure how the best way to do that would be. I can check when I get home, but that's about 15 hours from now :(

---

### Post by ankspo71 on 2010-01-18
Hi,
First, try this link...
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Then....
There are many-many different components to kde so the other advice I could come up with is, go to Synaptic Package Manager, to see if you can find out what was installed last. To do that, click on File, then History in the menu of synaptic. Once you have located the day where some kde parts were installed (hopefully it will be listed), remove each item one by one until you get most of them gone. The above link should give you a very good head start on this. Then finish off by re-installing the package called "ubuntu-desktop" to make sure nothing is missing. 
Hope this helps.

---

### Post by kireol on 2010-01-18
cool thanks :D

---

