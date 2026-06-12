---
title: "Ubuntu 11.10 hangs on shutdown."
date: 2012-03-14
forum: General Help
---

### Post by FenrirXIII on 2012-03-14
Specs.

Dell INSPIRON N5040
64-bit (400GB/4GB ram)
intel Core i3

as stated on the title, my 11.10 recently hangs on shutdown. While this is a rare case and doesn't frequently do so. I'm a bit concern if it become a problem later.

Now judging from my observation, it only hangs when a warning: _Unable to mount U3 System_ (**[COLOR=Red]SEE ATTACHMENTS BELOW[/COLOR]**). I did have a USB plugged in there when it occurred recently (and i can't remember if I did the last time it occur.) The USB pendrive was and is still working before I Safely Removed it. [COLOR=Navy]Pendrive is still mountable though after and still reads perfectly.[/COLOR] ACTUALLY PENDRIVE IS NOW NON-MOUNTABLE.

Theory:
USB Pendrive comes with a U3 System (_appearing to be a CD ICON on Filesystem_ categories) _won't unmount _(Eject/Safely Remove) stating that there a _job pending on dev/sr1_. If my theory is correct, Ubuntu is trying to shutdown making sure everything is ok to turn off.. but because of U3 couldn't be unmounted, Ubuntu is not allowing itself to shutdown. (just a theory thou... I'm barely learning the ropes on Linux computing)

Problem
On shutdown, Ubuntu 11.10 _hangs _(don't know if it's considered a freeze)_ on the exit theme_:
---------
ubuntu
 . . . . 
---------

while, or course, those _four circle still animating to change color_.

I don't always want to force shutdown (hold power button) every time this happens. [SIZE=3]so has any of you guys (and girls) figure out who to permanently solve this matter?[/SIZE]):P):P):P):P

---

### Post by tobiz on 2012-03-16
Try running "sudo /etc/init.d/networking stop", immediately before shutting down by either the gui or "sudo shutdown -h now".  Others have reported this solves the problem and it works for me. If it does work for you then all you need to do is work out a neat way of including this in the shut down script.

---

### Post by defg on 2012-07-26
Stopping the networking service/daemon/whatever with ```
sudo /etc/init.d/networking stop
``` and then shutting down with...```
sudo shutdown -h now
``` worked for me.

I have a 901 Eee PC with Mint 13 XFCE...this also happened with Ubuntu and Xubuntu (all 12.04). Thanks for the posts!

---

### Post by BigJules on 2012-08-05
Good one, Tobiz. 

Worked for me on 12.04 when I was being driven crazy after a RAID replace of a bad drive (thanks, Ubuntu RAID - didn't lose a 'bit' of data) and because the sys couldn't shutdown, it kept rebuilding from scratch at each power up.

---

