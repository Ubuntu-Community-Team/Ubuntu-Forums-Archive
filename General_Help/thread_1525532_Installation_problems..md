---
title: "Installation problems."
date: 2010-07-06
forum: General Help
---

### Post by RobLS on 2010-07-06
So I already had windows 7 installed on my raid. So I figured that I would install Ubuntu on my 250gb external. I burn it, boot to CD, and tell it to wipe and install the external hdd. After installation it prompts me to take out the CD, then press enter for it to restart. It restarts, gets all the way through and then says:

Error: no such device: f8b79a59-3c13-408a-b332-dd5e9dc37729. 
Grub rescue>

I am unfamiliar with this issue, and would have looked for a fix on my windows side, but now I am unable to boot into my windows side at all.

So I am in need of help, desperately.

If I can receive help as soon as possible that would be fantastic.

Thank You
Rob

---

### Post by garvinrick4 on 2010-07-06
You most likely did not on last page of install #8 I believe hit the advanced button and
install grub to sdb which is the drive you installed Ubuntu. I know nothing about raid so
I cannot surmise but if you want your dual boot to work use the boot info script in a Live Cd and
post on this thread. The other 2 are grub tutorials.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by RobLS on 2010-07-06
I am also unable to get into ubuntu. I put the cd back in and selected try ubuntu w/o installing, and its been at the loading screen for about 5 mins.

---

### Post by garvinrick4 on 2010-07-06
> **RobLS said:**
> I am also unable to get into ubuntu. I put the cd back in and selected try ubuntu w/o installing, and its been at the loading screen for about 5 mins. Loaded once for install should load aqain to Try Ubuntu (live cd).
If does not load and no one comes on thread that Knows raid then there is a way
to reinstall Windows boot manager.

---

### Post by RobLS on 2010-07-06
Looks like I need to reinstall windows now. I just noticed that for some reason, it separated my raid.  Looks like my ending question will be, how much space does 64 bit ubuntu take up, the latest 10.04 version?

---

### Post by garvinrick4 on 2010-07-06
> **RobLS said:**
> Looks like I need to reinstall windows now. I just noticed that for some reason, it separated my raid.  Looks like my ending question will be, how much space does 64 bit ubuntu take up, the latest 10.04 version? A install with all the bells and whistles only takes up at the most 5 gig. It is nice to just make it at least 8 gig and then it gives you the option of making a /home (your doc's, downloads, music ect. ect.)
As big as you need. If you want to use your install as the /home also make the install 
larger in gigs. And always remember in last page of install in advanced tab to put boot in sda if on internal
and sdb if a second drive and so on.

---

### Post by RobLS on 2010-07-07
My luck just gets worse and worse. The installer cd keeps either getting suspended or freezes. Extremely frustrating since now I don't have a computer to use. Waiting for a windows cd which I will hopefully get soon.

---

