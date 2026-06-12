---
title: "ATI drivers problem after new version"
date: 2012-01-06
forum: General Help
---

### Post by dhtj on 2012-01-06
Hi guys and girls,
I had beautiful Ubuntu 11.10 with KDE and Unity and i tried to install Gnome-Shell. I installed it without problems during installation, but after the restart when at the enter-session-screen i choosed Gnome and logged in there was poor visual efects and bad interface at all. I didn't picture it, but I'm sure it wasn't right. 
Then I searched at internet and I found the problem may be in drivers.
My video drivers was the default, that the system tell you to install at first boot at icon there to the clock :D
I downloaded the latest Catalyst drivers from the AMD site and I installed them following the instructions, but nothing good happened. Afer the reboot there was no picture on the screen. I booted "recovery mode" and in the command line type "sudo apt-get install fglrx" . With this I was again ot first step. 
I tried to install again the drivers, there was a problem again, and I don't know what exactly I did ( :D ) but the Ubuntu is not starting again. This shows when I type "startx":

[[img]http://store.picbg.net/thumb/82/7A/538149bcbfb2827a.jpg[/img]](http://picbg.net/img.php?file=538149bcbfb2827a.jpg)

Is there a solution? 
Thank you.

P.S. How is my English? :D

---

### Post by QIII on 2012-01-06
Every time I log into a GNOME session with AMD/ATI cards, it looks like doodoo.  So I stick to KDE.

I'm on my mobile, so I can't see the image well.  Are you left with a command line?

After you installed the driver, did you do

```
sudo aticonfig --initial
```

before shutting down?

Edit:  Come to think about it -- did you uninstall the previous driver first?

---

### Post by dhtj on 2012-01-06
> **QIII said:**
> Every time I log into a GNOME session with AMD/ATI cards, it looks like doodoo.
Monts ago I was using Fedora too. There wasn't problem with Gnome.

> **QIII said:**
> I'm on my mobile, so I can't see the image well. 
Text on the image is: [I]
Fatal server error: could not create lock file in /tmp/.tx0-lock
[/I]
> **QIII said:**
>  Are you left with a command line?
Only.

> **QIII said:**
> After you installed the driver, did you do

```
sudo aticonfig --initial
```

before shutting down? 
I think, I forgot : (

> **QIII said:**
> Edit:  Come to think about it -- did you uninstall the previous driver first?

First time yes. Result:0
Second time, they told me (from one forums) to leave the current driver without uninstaling it. The result is here :D

---

### Post by QIII on 2012-01-06
Ok.  There are two links I usually refer people to to get rid of the fglrx driver (the proprietary one) and restore the open source one.  You should be able to do it if you can get to the command line from recovery mode.

I'm on a cell phone on a train right now, so my browser is limited.  You can click my name at the left and click to see other posts I have made.  Sometime in the last couple of days I helped someone with a similar issue.

BUT before you do anything, use the Live CD to back up any important files.

Fedora worked months ago because it was still using GNOME2.  I use the KDE spin of Fedoraand have had a lot of problems with the proprietary drivers with it, so I use the open source one in Fedora.

---

### Post by QIII on 2012-01-06
OK.  Have a look at my post, #2, here:

[http://ubuntuforums.org/showthread.php?t=1904498](http://ubuntuforums.org/showthread.php?t=1904498)

---

### Post by Black_Sector on 2012-01-07
The Open Source ATI drivers work fine in Mint 12. They use Cinnamon, a fork of Gnome3, and I had no problems logging in either either the proprietary or OSS drivers for ATI.

However, using the proprietary drivers I couldnt play 3d games, like Urban Terror.....How do the OSS drivers work for gaming or video transcoding?

---

