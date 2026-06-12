---
title: "Bluetooth mouse stop working in Ubuntu 10.10"
date: 2010-10-14
forum: General Help
---

### Post by voronizer on 2010-10-14
Have strange issue after update to Ubuntu 10.10:
Mouse buttons (right and center) stop working after using keyboard.
After reconnecting nano-receiver mouse start working, but if you start using keyboard - mouse buttons stop working again.
Mouse&Keyboard model - A4Tech No any Lag Wireless Desktop GL-6630 ([http://www.a4tech.com/product.asp?cid=100&scid=156&id=600](http://www.a4tech.com/product.asp?cid=100&scid=156&id=600))

Tried to use it on another computer updated to Xubuntu 10.10 - works fine.

---

### Post by voronizer on 2010-10-14
> **voronizer said:**
> Have strange issue after update to Ubuntu 10.10:
Mouse buttons (right and center) stop working after using keyboard.
After reconnecting nano-receiver mouse start working, but if you start using keyboard - mouse buttons stop working again.
Mouse&Keyboard model - A4Tech No any Lag Wireless Desktop GL-6630 ([http://www.a4tech.com/product.asp?cid=100&scid=156&id=600](http://www.a4tech.com/product.asp?cid=100&scid=156&id=600))

Tried to use it on another computer updated to Xubuntu 10.10 - works fine.
The same issue with clean install Xubuntu 10.10.

---

### Post by toystoryii on 2010-10-15
Same here,

I've updated to 10.10 and using a PS2 mouse and USB Keyboard.

It seems only certain buttons on the keyboard work and right mouse click.  I am having another work colleague SSH to my box so I can shut things down to restart my machine without loosing work!

I've even plugged in a 2nd mouse as USB which does move the pointer, but has the same left, middle click problems.

Only a restart is helping! Please help anyone.

---

### Post by kiwi_steve on 2010-10-20
Similar problem for me, although my BT mouse needed to be reinstalled in the bluetooth manager (removed, then reinstalled) after each reboot otherwise it wasn't working  - once reinstalled it worked fine... until today.

Big pile of Ubuntu updates went in this morning, then I rebooted and I can no longer even reinstall the mouse.  Bluetooth finds it, but it fails the install.  Hardware is a Toshiba L650 laptop.  I'll keep looking, but thought I would post in case someone else is having similar problems

Steve

---

### Post by SiggSauer on 2010-10-22
Hey guys,

I've got a similar problem, I've got a Logitech MX1000 BT mouse.

Ubuntu recognizes the receiver and even sees the mouse when searching for BT devices, the problem is that that's all it does. It keeps asking if I should accept the mouse when I do accept it is just asks again.

I know there have been many issues with this, unfortunately not one of the previous solutions worked for me. The mouse works just fine under Windows XP, Vista and 7 though so it's definitely not broken.

---

### Post by gmc on 2010-10-22
You can add me to your list.

I'm on a Mac Mini (3,1) with a Microsoft Wireless 6000 keyboard and Logitech Bluetooth mouse. I can get the devices to sync, but after the goto sleep, I can't seem to wake them up. They both worked perfectly in 10.04.

Looks like something is broken in 10.10's bluetooth code.

G

Update: I use Duracell batteries (with the power test stripe on the side) in all of my devices. Checking the power level revealed that they showed 50% charge, so I decided to replace them with fresh ones. This appears to have solved my problem.

---

### Post by jnanes on 2010-10-22
Hello, 
 
I also have this issue. My Microsoft Bluetooth Elite Keyboard and Mouse both need to be manually reconnected after reboot, hibernate, or suspend in Ubuntu 10.10. Any help would be greatly appreciated!

---

### Post by kiwi_steve on 2010-10-25
An update to mine - I've done nothing, but a day of using Windows seems to have fixed it (who would have believed Windows could fix anything?):shock:...

I rebooted into Ubuntu again a day later and went through the usual remove and re-detect process and it worked.  Shut down, then restarted and the mouse actually fired up fine and has worked properly ever since.

I know that probably doesn't help anyone else, but the problem is sorted for me.  If anyone wants any particular config file contents or outputs to check against theirs then please ask and I'll provide what I can to help others.

Cheers

Steve

---

### Post by showgun22 on 2010-11-16
I have a Dell BT and most time it works at boot but every few times it starts very jerky all I have to do is using the mouse button turn off mouse and turn back on and it works as it should. I understand it is just an annoyance but this has been happening only since 10.10.....

---

### Post by el_sim0n on 2010-11-22
Same here with a bluetooth A4 mouse - left mouse button stops working after using the keyboard to log in.

EDIT: found this downloadatoz.c0m/driver/articles/fix-a4tech-left-click-not-working-in-ubuntu-10-10.html

THis helped me. Hope it does good for you, too./replace the 0 in *.com/

---

### Post by aapo4 on 2010-12-24
( EDITED: I read again what was wrote and found [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208) )

I just got A4Tech X7 GL-6630 -box. It contains keyboard and mouse. They are wireless and they are using same wireless-usb-dongle.
I have only tested this under Ubuntu 10.10.

First it seems to work, but if keyboard is used, left button of the mouse became to stick.

xinput list
shows two device. I thought one is keyboard and one is mouse.

If I disable keyboard with 
xinput set-int-prop ID "Device Enabled" 8 0 
-> I get mouse working, but then (of course) keyboard is not working.

---

### Post by aapo4 on 2010-12-25
Somebody have got this working just upgrading official packages.

Somebody have got this working with [https://edge.launchpad.net/~raof/+archive/aubergine/](https://edge.launchpad.net/~raof/+archive/aubergine/)

```
sudo add-apt-repository ppa:raof/aubergine
sudo apt-get update
sudo apt-get upgrade
```

I got my mouse+keyboard working with [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) (Read that before use)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```

---

