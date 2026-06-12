---
title: "Getting a black screen when booting sometimes"
date: 2011-02-01
forum: General Help
---

### Post by Tumling on 2011-02-01
I am as new as you can be with linux/Ubuntu.
And im not sure where to post this.

I just downloaded Ubuntu 10.10 Netbook.

Sometimes when i am start my netbook i boot to black screen.
I can hear the loading music but the screen is just black.
And when i press the powerbutton to close the computer and turn it on again, then sometimes i can see the screen and everything is working. and sometimes it is working just fine.

when i have my usb mouse and usb wireless network thingy it seems to have a hard time booting, but when i unplug my usb mouse and network thingy it boots just nice.


It would be nice if i could turn on the power and then the netbook would just startup and show me a screen, and didnt have to unplug my usb things first...

Can someone help me ?

---

### Post by Rubi1200 on 2011-02-01
Hi and welcome to the forums :-)

what graphics card do you have installed?

---

### Post by Tumling on 2011-02-01
Its an old laptop im working on...

So the gfx card is a "SiSM661MX integrated 3D graphics with 64MB shared memory"
The rest of the hardware can be found [here]("http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire3500/Aspire3500sp2.shtml")

---

### Post by Rubi1200 on 2011-02-01
You could try some of the options mentioned here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

I would start with nomodeset first and see where that gets you.

---

### Post by Tumling on 2011-02-02
i have tried all the things in the post
[SIZE=2][B]nomodeset
[/B][/SIZE][SIZE=2][B]acpi_osi=
[/B][/SIZE][SIZE=2]**Noapic and nolapic**[/SIZE]
**[SIZE=2]vmalloc=196[/SIZE]**

and nothing seems to make my computer work

---

### Post by Rubi1200 on 2011-02-02
Can you boot to recovery mode?

If yes, try this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot and try again.

---

### Post by tredegar on 2011-02-02
In my experience (10.04LTS on 4 very different computers) this is a new "feature" of ubuntu.

When boot fails, or hangs, I hold the power button down and then reboot again.
Eventually it works.

Probably problems with **upstart**, ubuntu's new way of booting, which does not seem to be totally relaible yet (but the problems are becoming less frequent).

Hope this helps.

---

### Post by Rubi1200 on 2011-02-02
> When boot fails, or hangs, [COLOR=Red]I hold the power button down[/COLOR] and then reboot again.
Eventually it works.

I was under the impression this *may* cause file-system damage?

A safer way would be:

Hold down the Alt + SysRq (Print Screen) buttons simultaneously and slowly type out R E I S U B

---

### Post by Tumling on 2011-02-02
> **Rubi1200 said:**
> Can you boot to recovery mode?

If yes, try this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```Reboot and try again.

When i wrote this at the end of the other text on a new line and pressed Ctrl + X i got a new screen where i could choose some things to do... i cant remember them now...
one of them was to make more free space i belive and a "boot normally" and that was the one i picked...

And then i had to login from the promte (is that what it is called ?)

---

### Post by Rubi1200 on 2011-02-03
I am not sure I understand. Are you able to boot normally now?

If not, have you tried anything else to get things going?

There might be some settings in BIOS to change the USB devices, so have a look and see if there is something that might help you.

---

