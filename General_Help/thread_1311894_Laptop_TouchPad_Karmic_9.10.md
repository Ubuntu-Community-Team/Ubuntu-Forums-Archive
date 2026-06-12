---
title: "Laptop TouchPad Karmic 9.10"
date: 2009-11-02
forum: General Help
---

### Post by rDwyP44y on 2009-11-02
I just updated two of my laptops
one which has (
[LIST]
[*]Ubuntu (installed with Wubi)
[*]Win XP
[/LIST]

and another with (which has been installed by 3 partitions)
[LIST]
[*]Win 7
[*]Win XP
[*]Ubuntu
[/LIST]

I updated the first one via *System > Update Manager* and seen the problem, then I did the second one also and got the problem again so i know for a fact that it isnt me!

[B]Right now both laptops work fine with  USB mouse, but no touchpad
[/B]


P.s. i have toggles the Fn keys to see if the touchpad was locked, no success.

---

### Post by S0n1C! on 2009-11-03
Hey, 

I'm having the exact same problem. I just updated and my touchpad on my laptop doesn't work.

Computer
Dell XPS M1330
Ubuntu 9.10

---

### Post by soapBAR2 on 2009-11-04
I also had problems with my touchpad after upgrading (it wouldn't work at all). I found a possible fix here (worked for me):

[http://danilogurovich.wordpress.com/2009/10/17/ubuntu-karmic-koala-9-10-beta-buggy-touchpad-behavior/](http://danilogurovich.wordpress.com/2009/10/17/ubuntu-karmic-koala-9-10-beta-buggy-touchpad-behavior/)

---

### Post by danill2008 on 2009-11-04
Yeah that one wil work

---

### Post by S0n1C! on 2009-11-04
Hey. I just found this post last night. However if you updated from Ubuntu 9.04, don't do this. Read Bob's comment about manually updating your kernal and adding it to your boot menu.

If you have done

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

make sure you delete the file

/etc/modprobe.d/psmouse.modprobe.

If you keep psmouse.modprobe and don't update add the new kernel to the menu.lst file then your scroll won't work, and your touchpad won't work properly. 

Hope this helps.

S0n1C!

---

