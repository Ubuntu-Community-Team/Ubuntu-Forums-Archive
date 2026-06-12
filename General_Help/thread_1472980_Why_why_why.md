---
title: "Why why why"
date: 2010-05-04
forum: General Help
---

### Post by cowboy7305 on 2010-05-04
Why do i have trouble opening my dvd drive When there is no disk in it 
is there a setting i have wrong or is it my dvd is packing up  it plays well and copies every thing i put at it, opens when i have disk in it but not when no disk in 
Help starting to PEE me off

---

### Post by TheNerdAL on 2010-05-04
Try rebooting, if that doesn't work, then the optical drive might be connected wrong or dead.

---

### Post by crlang13 on 2010-05-04
What model of drive is it?  Are you on a laptop or desktop - is it external?  If it's external, alot of drives will use phantom power via USB and there may be something funky going on when there is no disk in.

Also, define "trouble" :p

Also, is this a new problem or something that's been happening since you got the drive?

---

### Post by sxmaxchine on 2010-05-04
I dont know your how to fix the problem but try rightclicking the drive icon and clicking eject.

or add a launcher and add this command to it
sudo eject /dev/cdrom

---

### Post by RTrev on 2010-05-04
I have a hunch there might be something amiss in the latest kernels.  I suddenly began having problems where my DVD tray, on my pushing the button, would open about half way and then close immediately.  Doing it a second time works, as does using the eject command.

My friend who is running Arch happened to mention the same exact problem to me.  He's on the same kernel version.

I can't think of many other similarities between the systems, and the problem isn't identical to yours but seems similar.

I'd wait a bit, since there's going to have to be a new kernel soon anyway, given something about a vulnerability being found in the kernels up to and including .33 vintage.

hth

---

### Post by Ginsu543 on 2010-05-05
I too can confirm this somewhat. On my Apple keyboard, there is a button for dvd eject. It used to work great under 9.10 (I push it the drive opens, I push it again the drive closes, regardless of whether or not I have a disk in the drive), but now under 10.04, the button only works to open the dvd tray if there is media in it and then the button becomes non-operational once the media is removed. I'm hoping the devs will get around to fixing this regression, but I figure it's pretty low priority, so who knows?

---

### Post by rodh on 2010-05-05
I had that problem years ago on Window's 3.5,  may not be related at all but what we found at that time was a power control setting for the disk drive when idle. Of course this was a CD-ROM

---

### Post by cowboy7305 on 2010-09-26
Fixed it bought a new DVD drive

---

### Post by Quackers on 2010-09-26
Hmm I have a similar problem on my Vaio laptop. If there is no disc in the drive the eject button does not open the tray, but right-click and choosing "eject" does work. When there is a disc in the drive the eject button works. It's been like that the whole time I've had Ubuntu.

---

### Post by Chris1274 on 2010-09-26
I've had the same issue on my Dell with Ubuntu running on it. The eject hotkey doesn't work, but if I type 'eject' in a terminal the tray opens, even if there's no media in it.

---

