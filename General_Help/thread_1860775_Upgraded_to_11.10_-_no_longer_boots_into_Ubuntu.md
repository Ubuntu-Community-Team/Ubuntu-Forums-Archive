---
title: "Upgraded to 11.10 - no longer boots into Ubuntu"
date: 2011-10-15
forum: General Help
---

### Post by DrDaveyAtoms on 2011-10-15
I have upgraded from 11.04 to 11.10 this morning and after "restart(ing) to complete update" I am no longer able to boot into Ubuntu.

Specifically, after selecting the most recent kernel from the GRUB menu screen I get the Ubuntu logo with the four (?) red circles below. After this the screen flashes many times alternating between text and blank screen. I then see a window with a large red x on the left hand side reading "Cannot open theme file /usr/share/kde4/apps/kdm/themes/ethais". If I click the available button on this window the screen then proceeds to alternate between the text and the blank screen once more.

Does anyone know what is causing this problem? I always have issues when I update my kernel but on those occaisions I can always return to previous kernels and reinstall any missing files. I cannot do this now. The same thing happens with the three older kernels I have available.

I can boot into recovery mode and have been considering dumping all of my data to an extrnal disk and uninstalling Ubuntu and perhaps trying a fresh install (although this is possibly the last straw and I may return to Scientific).

Sorry for the long post. Can anyone help me? Has anyone also experienced this issue?

---

### Post by mörgæs on 2011-10-15
A fresh install is a good option. There is some advice regarding this in my signature.

---

### Post by DrDaveyAtoms on 2011-10-15
Yes thanks for the advice. Some good detailed information you have provided. I believe a fresh install will probably be for the best. I have been considering it for a while now. 

Just really dreading have to reinstall all those lib files which don't come as standard!!

---

### Post by hwttdz on 2011-10-15
Annoyingly this is the behavior you will get _on a fresh install from minimial_ if you use unity-greeter, lightdm, and the nvidia drivers/kernel modules.  

The way that I solved it was to get rid of unity-greeter and lightdm and install gdm (which surprisingly doesn't depend on everything gnome).  I guess you could go for xdm as well and give that a go.  And to do this hold shift as it boots and select the recovery kernel, remount as rw (this might just be a weirdness of my machine), and then drop to net root prompt.  And you should be able to manage what you need to from there.

I got this after upgrading, so I did a fresh install and was a little annoyed to see this after the fresh install.

Here's the bug report, may as well jump through the hoops of "this affects me too" [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/833619](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/833619)

---

