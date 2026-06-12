---
title: "Hard drive partitions are gone! sort of?"
date: 2009-08-01
forum: General Help
---

### Post by stuart.reinke on 2009-08-01
I'll admit that I didn't search for an answer to my problem before posting it.  I don't have any idea what happened or what terms to search for.

Here's my story.....
I decided to add a Windows XP installation to my computer. I want to use the BlackBerry sync software and can't get it to work with WINE.  "No big deal, I thought, I've temporally added Windows before. I happen to have 7Gb of unpartitioned space, I'll use that." 

I started the Windows installer, told it to use the unallocated space and thought that would be it.

I was wrong.

This time Windows wanted to write some files to the MBR (I expedted this)
however it also stated that it couldn't read the MBR and wanted me to repartition it. (not expected, didn't happen last time). I canceled the install process and rebooted.

Upon reboot I get an error message "Problem loading Operating System"

"No biggie, I thought, probably need to reinstall GRUB, I've done that before"

I was wrong

When I booted my Live CD here is what I found, and where my confusion starts.

I can mount the hard drive and everything is there.  (good news)

I thought maybe the boot flag got turned off so I started G-parted to check it out. 

G-parted shows the hard drive as one big area of free unallocated space.

there is supposed to be :
  Main partition with Jaunty installed
  Swap for Jaunty
  Another partition with Karmic installed
  Swap for Karmic
  Free space (unpartitioned)

What have I done? and how do I fix it? Please Help.

Have you ever been to the auto parts store and the clerk tells you "I'm sorry the computer says we are out of the part you need."  All the while you can see it sitting on the shelf behind him. That's how I feel.

thanks in advance for any help you can offer.

---

### Post by razorboy5 on 2009-08-01
what are u trying to install?

for me when i was trying to install XP
the installation did not find the SATA drive
so i had to manually install the SATA drivers in with the XP
to have it recognize my HD properly

hope this helps

---

### Post by stuart.reinke on 2009-08-01
> **razorboy5 said:**
> what are u trying to install?

for me when i was trying to install XP
the installation did not find the SATA drive
so i had to manually install the SATA drivers in with the XP
to have it recognize my HD properly

hope this helps

Never a problem detecting the HD. It seems that all or part of my partition table is gone.(a thought that just occured to me)

---

### Post by jerome1232 on 2009-08-01
Well partition tables are stored in the mbr if it somehow got borked I could see why everything would show up as unallocated.

I would suggest testdisk, install it on the live cd, (Yes you can install packages while running a live cd) it can recreate partition tables. I would also suggest runing smartmontools to make sure your disk isn't going out.

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by stuart.reinke on 2009-08-01
> **jerome1232 said:**
> Well partition tables are stored in the mbr if it somehow got borked I could see why everything would show up as unallocated.

I would suggest testdisk, install it on the live cd, (Yes you can install packages while running a live cd) it can recreate partition tables. I would also suggest runing smartmontools to make sure your disk isn't going out.

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

How do I install TestDisk?  I can't find it in Synaptic, and I don't see a .deb on their website. 

Also where do I install it to? I'm running on a live cd right now.

I think we're going in the right direction. I just need some more help to get there from here.

---

### Post by jerome1232 on 2009-08-01
```
sudo apt-get update; sudo apt-get install testdisk
```

It will get stored in ram, ram acts as a temporary file system while running the live cd.

---

### Post by stuart.reinke on 2009-08-01
Ok. I'll give it a try later today. Thanks for everything so far.

---

### Post by stuart.reinke on 2009-08-02
Well, I was able to et a partition table back. Never could get the computer to boot.  I'm sure with enough time (and help) I could have restored everything back to normal.  However, I really don't have time to dink with it so I just reinstalled my OS. everything was backed up anyway.

My thanks to jerome1232  there were a handfull of files that I hadn't backed up yet and was able to copy them to my flash drive before reformatting.

---

