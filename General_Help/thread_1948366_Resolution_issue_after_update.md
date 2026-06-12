---
title: "Resolution issue after update"
date: 2012-03-28
forum: General Help
---

### Post by idelosestados on 2012-03-28
Hi,

I updated the system (there was at least a new kernel and a chromium update) and after boot the resolution has been 800x600. I tried to go to the drivers-section in settings and it says that "no closed drivers are in use in this computer".

Besides the bad resolution, after the update mouse cursor is disappearing from time to time and chromium has had some issues (crashing repeatedly, also adblock is crashing).

Can someone help me with this?

---

### Post by colin.p on 2012-03-28
I run 10.04X86 on a server and when I get a kernel update, it throws off my resolution to 800X600 as well. The first couple of times, I re-installed my NVidia driver, but found that all I had to do was re-boot again and it put my resolution back to normal. 
When a simple re-boot stops working, then I will investigate further.

---

### Post by idelosestados on 2012-03-28
> **colin.p said:**
> I run 10.04X86 on a server and when I get a kernel update, it throws off my resolution to 800X600 as well. The first couple of times, I re-installed my NVidia driver, but found that all I had to do was re-boot again and it put my resolution back to normal. 
When a simple re-boot stops working, then I will investigate further.

Well, a reboot doesn't work for me unfortunately. This is the first time this has happened with Lubuntu in this netbook (Toshiba nb305-n310).

How do I re-install my driver?

---

### Post by raja.genupula on 2012-03-28
have you tried setting resolution with xrandr ? 
read this for more info 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by WasMeHere on 2012-03-28
> **idelosestados said:**
> Well, a reboot doesn't work for me unfortunately. This is the first time this has happened with Lubuntu in this netbook (Toshiba nb305-n310).

How do I re-install my driver?

If you want to install one of the built-in proprietary drivers, use ```
jockey-gtk
``` in most versions and flavours of Ubuntu.

This link shows how to install a proprietary driver downloaded directly from the hardware manufacturer (the link itself describes nVidia, but a link in the link describes ATI as well)
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1948324_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948324")

What graphics chip is it in your netbook? What version of Lubuntu are you running? Max resolution 800X600 makes me think of 10.04.

---

### Post by idelosestados on 2012-03-28
> **Olle Wiklund said:**
> If you want to install one of the built-in proprietary drivers, use ```
jockey-gtk
``` in most versions and flavours of Ubuntu.

This link shows how to install a proprietary driver downloaded directly from the hardware manufacturer (the link itself describes nVidia, but a link in the link describes ATI as well)
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1948324_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948324")

What graphics chip is it in your netbook? What version of Lubuntu are you running? Max resolution 800X600 makes me think of 10.04.

Graphic card specs from Toshiba website reads as: Intel® Graphics Media Accelerator 3150.

I've got the newest version of Lubuntu. The code you gave me gives the same response as opening the drivers-settings from menu: "no closed drivers are in use in this computer".

I will try the xrandr thing later today.

---

### Post by WasMeHere on 2012-03-28
> **idelosestados said:**
> Graphic card specs from Toshiba website reads as: Intel® Graphics Media Accelerator 3150.

I've got the newest version of Lubuntu. The code you gave me gives the same response as opening the drivers-settings from menu: "no closed drivers are in use in this computer".

I will try the xrandr thing later today.

OK, usually you don't need proprietary drivers with Intel Graphics. Have a try with xrandr, it will discover what is possible with the present setup. What do you mean by newest version of Lubuntu: ***11.10 or Precise beta (12.04)***? It might be worth trying a live session booted from a USB drive with the other one of those two versions. Right now I am testing Lubuntu Precise beta, and I like it very much.

---

### Post by idelosestados on 2012-03-29
> **Olle Wiklund said:**
> OK, usually you don't need proprietary drivers with Intel Graphics. Have a try with xrandr, it will discover what is possible with the present setup. What do you mean by newest version of Lubuntu: ***11.10 or Precise beta (12.04)***? It might be worth trying a live session booted from a USB drive with the other one of those two versions. Right now I am testing Lubuntu Precise beta, and I like it very much.

Writing 'xrandr' on the command line I get this:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0*
```

And from 'xrandr --output VGA1 --mode 1024x600' this:

```
xrandr: Failed to get size of gamma for output default
warning: output VGA1 not found; ignoring
```

---

### Post by WasMeHere on 2012-03-29
Obviously your highest available resolution is 800x600. I don't know how to repair it. Maybe the easiest way would be to try a live session booted from a CD or USB drive. Maybe you can try more than one version: Lubuntu 11.10 and Lubuntu Precise beta daily build (12.04). 

And if a live session works, save your personal files and then install that version. This is what I would do, but it is some work to do. Let us hope someone else can give efficient help to repair your present installed version.

---

### Post by idelosestados on 2012-03-29
> **Olle Wiklund said:**
> Let us hope someone else can give efficient help to repair your present installed version.

Which by the way is the Lubuntu Precise beta daily build (12.04) as of now that I tried to repair the 11.10 by updating it. Didn't work.

But thanks for your effort anyway.

---

### Post by WasMeHere on 2012-03-30
> **idelosestados said:**
> Which by the way is the Lubuntu Precise beta daily build (12.04) as of now that I tried to repair the 11.10 by updating it. Didn't work.

But thanks for your effort anyway.

Hi again idelosestados,

Sorry that my tips didn't work. But after a night's sleep I have some ideas, that might be worth trying.

1. What about a live session booted from the install CD or USB drive? Will you get better graphics? If this is the case, it would probably help to make a fresh install.

2. Maybe you should try some other distro, that might co-operate better with your hardware.
- Linux Mint (standard) [[COLOR="RoyalBlue"]_http://www.linuxmint.com/download.php_[/COLOR]]("http://www.linuxmint.com/download.php") or
- Linux Mint Debian [[COLOR="RoyalBlue"]_http://www.linuxmint.com/download_lmde.php_[/COLOR]]("http://www.linuxmint.com/download_lmde.php")

Have fun finding out
Olle

---

### Post by idelosestados on 2012-03-30
> **Olle Wiklund said:**
> Hi again idelosestados,

Sorry that my tips didn't work. But after a night's sleep I have some ideas, that might be worth trying.

1. What about a live session booted from the install CD or USB drive? Will you get better graphics? If this is the case, it would probably help to make a fresh install.

2. Maybe you should try some other distro, that might co-operate better with your hardware.
- Linux Mint (standard) [[COLOR="RoyalBlue"]_http://www.linuxmint.com/download.php_[/COLOR]]("http://www.linuxmint.com/download.php") or
- Linux Mint Debian [[COLOR="RoyalBlue"]_http://www.linuxmint.com/download_lmde.php_[/COLOR]]("http://www.linuxmint.com/download_lmde.php")

Have fun finding out
Olle

Yep, live session from USB works fine, so a fresh install it will be then...

I hope this problem doesn't show up too frequently or I'll have to - gasp - resort to some capitalist software. :cry:

---

### Post by JC Cheloven on 2012-03-30
Hi, you could try to delete (or move away) the file ~/.config/monitors if it exists, and reboot. 

Also you may find inspiring posts like [this one]("http://ubuntuforums.org/showthread.php?t=1820298"). To sum up, what realzippy (a knowledgeable user over here) posted was:

1) Create a new resolution mode. In their case of 1440x900:
```
xrandr --newmode  1440x900_60.00   106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```
2) Make this mode avilable for the desired output (in that case VGA-0, for you it should be 'default' I think):```
xrandr --addmode VGA-0  1440x900_60.00
```
3) Choose that mode for your output. In the case of the example:```
xrandr --output VGA-0 --mode 1440x900_60.00
```
Not an exact solution for you, as you'd have to adapt it, but perhaps it points you in the right direction. 

Best
JC

---

### Post by WasMeHere on 2012-03-31
> **idelosestados said:**
> Yep, live session from USB works fine, so a fresh install it will be then...

I hope this problem doesn't show up too frequently or I'll have to - gasp - resort to some capitalist software. :cry:
When you get used to linux, you will find it more stable than any proprietary operating system. It depends also on what you do with it: you can take risks or avoid risks, when installing and tweaking the system. If you take regular backups (and an extra backup when you try something risky), you'll have peace of mind.

And if you want stability, I suggest that you stay with Ubuntu's LTS versions. The coming one, 12.04 is an LTS version with support during 5 years.

---

### Post by idelosestados on 2012-04-01
> **Olle Wiklund said:**
> When you get used to linux, you will find it more stable than any proprietary operating system. It depends also on what you do with it: you can take risks or avoid risks, when installing and tweaking the system. If you take regular backups (and an extra backup when you try something risky), you'll have peace of mind.

Well, this flavor of linux seems to be unstable if stable means that updates won't break some parts of the system. Also there's smaller things, such as suspend/hibernate issues. Of course I understand that free software can't be perfect though.

> And if you want stability, I suggest that you stay with Ubuntu's LTS versions. The coming one, 12.04 is an LTS version with support during 5 years.

I liked 10.04 LTS but I updated it to newer versions and they weren't as nice. I began to bump to strange bugs that I didn't have time to solve. I think I'm going to go for fluxbox-mint next.

---

### Post by WasMeHere on 2012-04-02
> **idelosestados said:**
> Well, this flavor of linux seems to be unstable if stable means that updates won't break some parts of the system. Also there's smaller things, such as suspend/hibernate issues. Of course I understand that free software can't be perfect though.

I liked 10.04 LTS but I updated it to newer versions and they weren't as nice. I began to bump to strange bugs that I didn't have time to solve. I think I'm going to go for fluxbox-mint next.

No software is perfect. Find a distro that cooperates well with your hardware, and has an interface that appeals to you ... and is stable enough! By the way, if you want stability, try Debian Stable! It lacks some of the new bells and whistles, but it is super stable. Use it if it can do what you need!

Good luck with Linux Mint :-)

---

