---
title: "Installing Ubuntu + VNC on laptop only using VGA mode"
date: 2011-07-24
forum: General Help
---

### Post by Baphomet on 2011-07-24
**Intro:**
The graphic card on my Asus A8Js died and now i'm left with a perfectly good laptop (everything except the graphic card works) that is too expensive to repair! I got a new one already since I really need it for working.

**State of things:**
I'm able to boot on to the winxp which is currently installed by plugging another monitor to the VGA exit on the laptop, but only into to VGA mode and with some artifacts running through the screen (lines and dots and what not). If I let it boot in normal mode I stop getting signal on the external monitor and that's it.

**Help with:**
I would like to know If it is possible to do a full installation of Ubuntu on this laptop and then run with normal GUI but on VGA mode to then install VNC or something of the kind. VNC would permit me to use the computer without an external monitor and thus install and manage more stuff. 

I guess that a command line only install of ubuntu would also be another option, but I'm not that fluent with command line.

Thank you for your time.

A8Js hardware description: [http://www.notebookreview.com/default.asp?newsID=3313&review=Asus+A8Js](http://www.notebookreview.com/default.asp?newsID=3313&review=Asus+A8Js)

---

### Post by bakegoodz on 2011-07-24
I not confident that you can get it to work. I've seen a couple of video cards go bad like this. The VGA mode in Windows working is kinda of a fluke it uses only enough of the bad card to not crash (Bad Video RAM?) Linux access the card a little differently and I couldn't get Linux to every work with these bad cards. You can try setting VGA as the hardware in the xorg.conf, but my experience is Xorg ignores what you set there does its own thing. I really hate the Xorg auto configure its had the past couple of years.

---

### Post by Baphomet on 2011-07-25
Well that´s kind of depressing! How about text based install? What do you think?

Thank you!

---

### Post by bakegoodz on 2011-07-25
Ubuntu server would probably work. A Command install from the desktop CD might use a graphical boot screen possibly causing problems.

---

### Post by Baphomet on 2011-07-26
So, unless some magic happens, it's probably better to forget about this!

Thank you once again!

---

### Post by linuchsan on 2011-07-26
Maybe you can get the harddrive out, put it in an other laptop. Install the base system with ssh. Put the hd back again and boot broken laptop. Login (wired) and finish it by install what you want.

---

### Post by Baphomet on 2011-07-26
And what about all the new hardware? Using that method would the ethernet card be installed without any input from me?

---

### Post by linuchsan on 2011-07-26
If your laptop worked out of the box, I don't see any problems. It will work ;-)

---

### Post by Baphomet on 2011-08-20
Hello again! I tried the tactic of installing to the hard drive from another computer first but am having some trouble with this. I've used the minimal CD and the alternate CD to install a CLI only version, but when the computer reboots (after installation is finished) it starts to boot up and only some strange coloured vertical lines are shown. These lines are about a character's heigh and only three or four rows are there.

What could this be? There was no error during installation! And it's the same behaviour with both versions of installation source.

---

### Post by Duncan Williams on 2011-08-20
My thoughts on the matter, given that I had a dead graphics card awhile back on a desktop pc.
If you can boot and run from livecd.
Linux may go into software rasterising for the vga output and basically bypass the card/chip.
If you get a gui from running off cd/usb stick, then you may be able to install and run a linux distro with limited resolution (should be able to get 1080by768 say.

I was able to do that in windows and linux with my dead card (it just used the vga port but in software mode.

If you can't get anything showing from the live-cd then your next step would be to get a cheap secondhand replacement graphic card/chip from ebay or wherever on the net.

---

