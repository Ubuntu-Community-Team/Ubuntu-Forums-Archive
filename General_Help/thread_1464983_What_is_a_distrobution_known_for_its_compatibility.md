---
title: "What is a distrobution known for its compatibility? (mainly with LCD monitors)"
date: 2010-04-28
forum: General Help
---

### Post by princerameses on 2010-04-28
I have an e-machines flat pannel monitor and I often find it's not supported. That, or I have to use 800x600 resolution. I'm on XP right now on a compaq and I have to settle with 1024x768. Which is stretched out. I also use a linksys USB adapter for internet and it must work with-out effort on my part. It works with the latest versions of ubuntu, puppy, Damn Small Linux and a few others. 

Are there any distros that might work for me? And by the way, I get the correct resolution (I can't remember what it is) with my e-machines W3052.

---

### Post by CharlesA on 2010-04-28
Sounds like you need the correct video driver. I only had problems with my widescreen LCD when I didn't have the right video driver installed (that was back in Ubuntu 8.04).

Ubuntu should work, but what video card do you have?

---

### Post by princerameses on 2010-04-28
How do you find out?

---

### Post by CharlesA on 2010-04-28
Run this in a terminal window and paste the results:

```
lspci
```

---

### Post by princerameses on 2010-04-28
Well, I'm in XP right now.. What does the latest version of ubuntu use? And I actually prefer Xubuntu. Or is there a way to strip down ubuntu for older computers? (mines not THAT old, but I'd like it as minimal as possible)

Oh and when is 10.04 being released? Because I should probably wait until it's out before I get it if it's soon. ;)

---

### Post by CharlesA on 2010-04-28
I've heard good things about [lubuntu]("http://lubuntu.net/"). Ubuntu uses GNOME, and Kbuntu uses KDE. I really only have experience with the Gnome version of Ubuntu.

If you are in XP, you can check under device manager for "display adapters"

That should tell you what you have.

---

### Post by princerameses on 2010-04-28
S3 Graphics ProSavageDDR.

---

### Post by CharlesA on 2010-04-28
Wow, that's an old card. I don't know if there are any drivers for it.

You could try downloading and booting off of a Ubuntu live cd and see if you get the correct resolution.

---

### Post by princerameses on 2010-04-28
:(

That's why I'm asking for distros that are notorious for compatibility. :)

---

### Post by CharlesA on 2010-04-28
Only real way is to see if it works. :)

10.04 is being released some time tomorrow.

---

### Post by princerameses on 2010-04-28
Well, I don't want to waste a bunch of disks.. :roll:

I guess I'll download ubuntu tomorrow and see if I at least get 1024x768. It'd be nice if I could at least squish it together a little. Like have the display in the center of the screen and black on both sides so it doesn't stretch out. That's what my other monitor does. Well, it's a TV technically..

---

### Post by CharlesA on 2010-04-28
I'd say boot to USB, but I doubt that PC can boot off USB. Maybe use a CD-RW instead of a regular CD-R?

---

### Post by -humanaut- on 2010-04-28
That is an ancient card. Vesa might be your only option what resolution are you seeking? how big is your monitor?

---

### Post by princerameses on 2010-04-28
It might be 1280x800. I'm not sure. What's vesa?

---

### Post by CharlesA on 2010-04-29
Just the name of the driver.

[http://linux.die.net/man/4/vesa](http://linux.die.net/man/4/vesa)

---

### Post by princerameses on 2010-05-02
I'm in ubuntxu right now. (live CD) 
It is using 800x600. Every distro I've tried with this computer + monitor have been 800x600. Is it a new video CARD I need? Or is there any way to get a driver for the card I have that will give me the correct res?

What if I got a different flat panel monitor? I see them at thrift stores sometimes.

---

### Post by princerameses on 2010-05-04
Bump. -sorry, need to-

---

### Post by Untitled_No4 on 2010-05-04
1. Do you have an /etc/X11/xorg.conf file? If yes, post its contents here.
2. In terminal, enter
```
xrandr
```
and post the output here.

---

