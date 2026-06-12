---
title: "wacom tablet"
date: 2010-04-29
forum: General Help
---

### Post by Nightwalker993 on 2010-04-29
i have a wacom pen and touch tablet and am running 10.4 what is the easy way to install and get it working? thanks :)

---

### Post by Merovius on 2010-04-29
Try here,

[http://ubuntuforums.org/showthread.php?t=1462026&highlight=wacom]("http://ubuntuforums.org/showthread.php?t=1462026&highlight=wacom")

---

### Post by Nightwalker993 on 2010-04-29
i dont have an ratio problem it does not work at all when i plug it in :(

---

### Post by Merovius on 2010-04-29
There were other links there that I thought might help. Didn't actually go through them all. Unless I am mistaken it should at least be detected and work. Maybe not complete functionality but at least work. I would search the forum for "wacom tablet" or "wacom tablet" & "karmic" I will look too.

---

### Post by Nightwalker993 on 2010-04-29
i did and the light comes on but not detected... i really need this for my art

---

### Post by egalvan on 2010-04-29
Two different Wacom's tested...

One a high-end with multiple buttons, and pressure-sensitive pen...
(Saphire-something, I believe)

the other a simple tablet, no extra buttons...

Both plugged-and-played...

GIMP saw them, and used them.

Gave the good one to my brother, he's a professional photographer...
lent the other to a student...

---

### Post by Nightwalker993 on 2010-04-29
well mine is not plug and playing and gimp not doing anything...

---

### Post by Favux on 2010-04-29
Hi Nightwalker993,

With a Bamboo P & T you're dealing with a new model that isn't quite fully supported yet, almost there.

Ping just submitted a patch to update gesture support and it looks like it will be accepted with a few changes.  Since xf86-input-wacom 0.10.6 was just released you'll want to clone from the git repository as soon as the patch is accepted and commited.  This gets you the X driver that works for Xserver 1.7.

In the meantime the stylus should be working with the default xf86-input-wacom 0.10.5 in Lucid.  Just with touch not working so well.  I'm not sure which version of wacom.ko (the usb kernel driver/module) is default.  It sounds like maybe it is too old to support usb communication for your P&T.  So you probably need to compile linuxwacom 0.8.6 just for the wacom.ko, not to "sudo make install" it.  See the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") on how to do this.

---

### Post by egalvan on 2010-04-29
> **Favux said:**
> Hi Nightwalker993,

With a Bamboo P & T **you're dealing with a new model** that isn't quite fully supported yet, almost there.

Agreed, mine are older models, although both were still retailing on Wacom's site when I acquired them (pawn-shop specials) late last summer (prob around October

But also agreed, the basic function should be working...

try it on a Windows machine...
that is how I tested mine...
got the basic drivers and tested with MS-Paint on XP.
I know some folks frown on this attitude, but it assured me that the hardware was working, and that I was chasing the proper geese.

---

### Post by Favux on 2010-04-29
Hi egalvan,

I'm not one of them.  Dual booting allows you to check hardware, like you say, and update the bios along with many other advantages.

---

### Post by Nightwalker993 on 2010-04-29
it works fine on windows i followed those instructions... still nothing

---

### Post by knozos on 2010-04-29
I have an Intuos4 and only works x/y position, click, right click., and that's not enough for me, now i need to return to windows for designing.


I think I wrote correctly

---

### Post by Favux on 2010-04-29
Hi Nightwalker993,

> i followed those instructions
Wnat do you mean?  What did you do?  If you compiled and installed a 0.8.6 wacom.ko let's see if it is auto-loading:
```
lsmod | grep [Ww]acom
```


Hi knozos,

Welcome to Ubuntu forums!

Your Intuos4 should be fully supported.  Are you sure it was the linuxwacom driver that had your tablet?  You can check Xorg.0.log in /var/log.  You just may need to set up a script of xsetwacom commands to get the functionality you want, since there isn't a wacomcpl for Lucid yet.

Hope this helps.

---

### Post by knozos on 2010-04-30
> **Favux said:**
> Hi Nightwalker993,


Wnat do you mean?  What did you do?  If you compiled and installed a 0.8.6 wacom.ko let's see if it is auto-loading:
```
lsmod | grep [Ww]acom
```


Hi knozos,

Welcome to Ubuntu forums!

Your Intuos4 should be fully supported.  Are you sure it was the linuxwacom driver that had your tablet?  You can check Xorg.0.log in /var/log.  You just may need to set up a script of xsetwacom commands to get the functionality you want, since there isn't a wacomcpl for Lucid yet.

Hope this helps.

i tried some xsetwacom commands and always said: "error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory"

---

### Post by Favux on 2010-04-30
Hi knozos,

That doesn't make sense.  That's with Lucid (10.4) and the default xf86-input-wacom?  That's saying your missing a library, which is something you might see if you compiled the driver yourself.  Check in Synaptic Package Manager that xserver-xorg-input-wacom is installed.

---

### Post by knozos on 2010-05-01
> **Favux said:**
> Hi knozos,

That doesn't make sense.  That's with Lucid (10.4) and the default xf86-input-wacom?  That's saying your missing a library, which is something you might see if you compiled the driver yourself.  Check in Synaptic Package Manager that xserver-xorg-input-wacom is installed.

yes, it's the default [IMG]http://img94.imageshack.us/img94/25/seleccin001.jpg[/IMG]

---

### Post by Favux on 2010-05-01
Hi knozos,

Well, there you go.  I still don't understand it.  I would assume a defective installation and tell Synaptic to reinstall xserver-xorg-input-wacom and then reboot.

If that doesn't work you could try installing all the dependencies/libraries I've identified for xf86-input-wacom and rebooting:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libncurses5-dev xutils-dev autoconf libtool pkg-config

```
I don't know if after the fact (compile) library installation will work.

---

### Post by knozos on 2010-05-02
> **Favux said:**
> Hi knozos,

Well, there you go.  I still don't understand it.  I would assume a defective installation and tell Synaptic to reinstall xserver-xorg-input-wacom and then reboot.

If that doesn't work you could try installing all the dependencies/libraries I've identified for xf86-input-wacom and rebooting:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libncurses5-dev xutils-dev autoconf libtool pkg-config

```
I don't know if after the fact (compile) library installation will work.

Now works!
[IMG]http://img26.imageshack.us/img26/1994/itworks.jpg[/IMG] 
x/y position, pen pressure, tilt, eraser, pan, right click, everything works well

---

### Post by Favux on 2010-05-02
Hi knozos,

That's great!  :D

Which worked, reinstalling xserver-xorg-input-wacom or getting the libraries?

---

### Post by knozos on 2010-05-03
> **Favux said:**
> Hi knozos,

That's great!  :D

Which worked, reinstalling xserver-xorg-input-wacom or getting the libraries?

reinstalling xserver-xorg-input-wacom

---

