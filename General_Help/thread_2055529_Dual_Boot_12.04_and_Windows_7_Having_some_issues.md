---
title: "Dual Boot 12.04 and Windows 7: Having some issues"
date: 2012-09-09
forum: General Help
---

### Post by Beardy42 on 2012-09-09
Namely that after installing Ubuntu 12.04 and going to log in, I am met with a frozen slate of a desktop in which nothing loads (at longest I've sat for 30 minutes, reading, whilst nothing changes) and only the mouse moves.

Its not a blank screen, its the desktop that one is normally greeted with, just with nothing loaded.

So far I've tried [http://askubuntu.com/questions/157158/desktop-will-not-load-after-12-04-upgrade](http://askubuntu.com/questions/157158/desktop-will-not-load-after-12-04-upgrade)
 and [http://askubuntu.com/questions/147285/unable-to-boot-into-ubuntu-12-04](http://askubuntu.com/questions/147285/unable-to-boot-into-ubuntu-12-04)
with no luck on either end (The first test saying that the xorg.conf doesn't exist.)

I've reinstalled it twice, tried a new disc, and still have had no luck whatsoever.

I figure it might be my graphics card (AMD Radeon HD 6900) not having its drivers automatically installed, so I have the file required to actually get them installed on my usb drive, I just can't open said drive to actually install... (See: desktop may as well be just an image where nothing loads or moves, aside from mouse.)

Really sad times...

So, any clue what to do?

---

### Post by dragonfly41 on 2012-09-09
Welcome to the "dual boot club".  My dual boot is down at the moment.

A few trouble shooting suggestions ..

From frozen ubuntu desktop can you get into terminal (tty mode) using Ctrl+Alt+F1
.. then exit tty by typing Alt+F7?

If you get into tty mode can you run some commands?   Such as copying files?

Can you reboot into Windows via dual boot menu?

Can you while in windows install a linux file system viewer to inspect your ubuntu installation (you give one clue that it is on a usb drive).. 
examples here
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)
[http://www.howtogeek.com/howto/33387/how-to-browse-your-linux-partition-from-windows/](http://www.howtogeek.com/howto/33387/how-to-browse-your-linux-partition-from-windows/)

Can you boot up a live ubuntu CD and get that desktop working?

Can you burn boot-repair-disk onto CD from running windows?

---

### Post by Beardy42 on 2012-09-09
I can boot into windows (its what I'm on right now, actually) and I can burn what discs as needed (I used a disc to install in the first place, and now own 2 working discs and one failed).

Turns out I can enter into that tty mode, I just have no idea what to do from there >.>.

The usb drive just has the driver for my graphics card on it. The actual ISO is on the discs I burnt.

---

### Post by Epodx64 on 2012-09-09
When your at the login menu right click on the Ubuntu dealy and switch it to 2d unity then run jockey after you login to download the ATI drivers.

---

### Post by Beardy42 on 2012-09-09
RIGHT! That last one finally got me in. So now I'm having the problem of "Sorry, installation of this driver failed."

At least I'm actually on the desktop now..

Edit: Eh, just gonna let the installer run while I enjoy UBUNTU. F***ing finally able to enjoy this lovely bit again.

---

### Post by Epodx64 on 2012-09-10
Try grabbing the newer Ati drivers from x-swat/x-updates i've had fairly good luck with those over the outdated drivers ubuntu offers here's a link:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

add the ppa then sudo apt-get update then see if Jockey has detected them

---

