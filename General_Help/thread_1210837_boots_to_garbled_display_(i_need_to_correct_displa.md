---
title: "boots to garbled display (i need to correct display settings)"
date: 2009-07-11
forum: General Help
---

### Post by ralphmcknight on 2009-07-11
All was fine, and then i went into the screen saver menu and selected one...

Now i boot into corrupt looking screen display.

I have run "dpkg-reconfigure xserver-xorg" several times from boot recover option, but i have never been asked any questions re the video settings or card etc?

I have just installed ubuntu - and am now deeper than i ever wanted to go :-)  just like with windows?

Is there anything else i can try, other than a complete new install?

Thanks in advance for any help.

---

### Post by utnubuuser on 2009-07-11
if your're in gnome, you might check "/etc/X11 to see if there's a backup copy from before you made changes to your xserver-xorg file

---

### Post by ralphmcknight on 2009-07-11
i am using the default desktop, i suspect there are no bakups - how would i check?

also - why is it that i dont get any video questions using ...reconfigure...
i only get keyboard and language etc questions?

---

### Post by Frugoo Scape on 2009-07-11
Just reinstall xorg and reconfigure it.

Well since I don't use Ubuntu anymore, I use arch linux here is what I would do on my first try on Ubuntu.

**If you think a file is messed up:**
sudo apt-get install xorg

**Delete your current xorg config:**
sudo rm /etc/X11/xorg.conf

You can reconfigure it, **but you won't need to**:
xorg --configure
sudo mv xorg.conf /etc/X11/xorg.conf

---

### Post by ralphmcknight on 2009-07-12
thankyou - i completely gave up, deleted all the partitions and reloaded from scratch.

as all my data was in a separate partition (as recommended by this forum - thanks guys), i lost no data!

Anyway - im back up and running.  I will try your "re-install the xorg" next time.  I wish i had given it a go this time.

---

### Post by TeamJ on 2009-07-12
graphics is a tricky one. with other problems you can use the GUI. with this the GUI is often inaccessible until you fix the problem so you have to use command line. when I did this I reinstalled too.

---

