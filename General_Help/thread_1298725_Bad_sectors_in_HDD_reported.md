---
title: "Bad sectors in HDD reported"
date: 2009-10-23
forum: General Help
---

### Post by Tapas Bose, India on 2009-10-23
Hallo everybody.
I have upgraded my Ubuntu 9.04 into Karmic on yesterday night. After the first boot Karmic gave me an warning. Palimpsest informed me that I have bad sectors in my HDD. In its status report the Reallocated Sector Count gives Warning Assessment, Value :
Normalized:  100
Worst:          100
Threshold:    5
Value:          65543 sectors
[Please see the screenshot]
I am very much worried. Today I installed GSmartControl via Synaptic. And run an Extended self test. The report is given as attachment.
Now what should I do now?
Is there any way to get rid of these bad sectors? Please help me.

---

### Post by earthpigg on 2009-10-23
your attached image is to small to read.

moving on from that:

bad sectors indicate ***physical*** hard drive damage - even with normal use, this eventually is 100% bound to happen at some point.

there are methods to tell the OS not to use those sectors, but that is a temporary fix... once sectors start failing, its only a matter of time before more and more do so and the hard drive becomes a brick or table weight.

if it's still under warranty, have it replaced.

if not, purchase a new hard drive.

if you really want us to tell you how to tell the OS not to use the bad sectors, we will do so... but, as i said, once one sector goes bad, more will soon follow. 

i suggest you back everything up immediately and start booting from and using a persistent thumb drive until you can get around to purchasing and isntalling a proper new hard drive. your local mom & pop computer shop can do this, if you do not want to.

make sure you protect against ESD if you decide to remove and replace the failing hard drive yourself.

---

### Post by earthpigg on 2009-10-23
ill point you in the right direction for the temp fix, if you really want to go that route:

[http://en.wikipedia.org/wiki/Badblocks](http://en.wikipedia.org/wiki/Badblocks)

---

### Post by Tapas Bose, India on 2009-10-23
Thank you for reply. I have dual boot pc with win xp. I executed CHKDSK from xp but it show me that I have 0 kb bad sector. What about that?

---

### Post by Tapas Bose, India on 2009-10-23
> **earthpigg said:**
> ill point you in the right direction for the temp fix, if you really want to go that route:

[http://en.wikipedia.org/wiki/Badblocks](http://en.wikipedia.org/wiki/Badblocks)
I saw man e2fsck. But I can not able to figure out which option should I use. Can you please give me the command?

---

### Post by P4man on 2009-10-23
Harddrives automatically remap bad sectors. Every disk, even a new one has some bad sectors and a lot of spares. This is not normally visible to the OS (except through SMART), the drive itself manages it and will remap bad sectors with spare ones. Its only when it runs out of spare sectors that the OS (chkdsk or  e2fsck) will start seeing it.

Now what you see here is warning from reading SMART data (Self Monitoring Ah;; something) which indicates that a lot of spare sectors are already being used, which points to imminent drive failure, There is nothing you can or should do, other than backup and prepare for the fact your drive is about to fail and will soon begin generating bad sectors (visible to the OS)

---

### Post by Tapas Bose, India on 2009-10-23
> **P4man said:**
> Harddrives automatically remap bad sectors. Every disk, even a new one has some bad sectors and a lot of spares. This is not normally visible to the OS (except through SMART), the drive itself manages it and will remap bad sectors with spare ones. Its only when it runs out of spare sectors the the OS will start seeing it.

Now what you see here is warning from reading SMART data (Self Monitoring Ah;; something) which indicates that a lot of spare sectors are already being used, which points to imminent drive failure, There is nothing you can or should do, other than backup and prepare for the fact your drive is about to fail and will soon begin generating bad sectors (visible to the OS)
Thank you for reply. I will do it.

---

### Post by az on 2009-10-23
Your drive is made by Hitachi?  Check to see if your drive is still under warranty:

[http://www.hitachigst.com/portal/site/en/menuitem.4e6284c20a3050a7760062f6aac4f0a0/](http://www.hitachigst.com/portal/site/en/menuitem.4e6284c20a3050a7760062f6aac4f0a0/)

---

### Post by P4man on 2009-10-23
> **az said:**
> Your drive is made by Hitachi?  Check to see if your drive is still under warranty:

[http://www.hitachigst.com/portal/site/en/menuitem.4e6284c20a3050a7760062f6aac4f0a0/](http://www.hitachigst.com/portal/site/en/menuitem.4e6284c20a3050a7760062f6aac4f0a0/)

Would be quite interesting to find out if they replace a drive because smart monitoring reports imminent failure. Strictly speaking, the drive isnt malfunctioning  yet.

---

### Post by az on 2009-10-23
> **P4man said:**
> Would be quite interesting to find out if they replace a drive because smart monitoring reports imminent failure. Strictly speaking, the drive isnt malfunctioning  yet.

SMART is giving a warning.  If the drive is still in the warranty period, they usually will.  That's what SMART is for...

This has been my experience from Canada.  Their warranty policies may be different in other countries.

---

### Post by gtaluvit on 2009-10-23
I just got the same problem. 72 million bad sectors? I don't think so. Looks like a bug.

---

### Post by Tapas Bose, India on 2009-10-24
> **gtaluvit said:**
> I just got the same problem. 72 million bad sectors? I don't think so. Looks like a bug.
Can you please tell me how many days ago you got the report and did you take any action?

---

### Post by P4man on 2009-10-24
Definitely a bug yes. I should have looked closer at the actual count on the OP's screenshot, but it was so low res it hurt my eyes and I just focused on the bold red text. Turns out he would have 65500 relocated sectors, which just as bogus. FWIW my drive has 100 spare sectors.

---

### Post by sisco311 on 2009-10-24
it's probably a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136")

---

### Post by Tapas Bose, India on 2009-10-24
> **P4man said:**
> Definitely a bug yes. I should have looked closer at the actual count on the OP's screenshot, but it was so low res it hurt my eyes and I just focused on the bold red text. Turns out he would have 65500 relocated sectors, which just as bogus. FWIW my drive has 100 spare sectors.
Thank you very much. You make me relaxed. I was too much worried about my machine. Thank you.

---

### Post by P4man on 2009-10-24
Its good to worry about it. In the sense that it encourages you to make backups which is always a good idea. Harddrive crashes often come out of nowhere.

---

### Post by Tapas Bose, India on 2009-10-24
> **P4man said:**
> Its good to worry about it. In the sense that it encourages you to make backups which is always a good idea. Harddrive crashes often come out of nowhere.
I pray all the time to god that to keep my machine healthy, because I love her very very much. That is why I am so much worried. Please don't mind anybody.

---

### Post by CharlesA on 2009-10-24
> **az said:**
> Your drive is made by Hitachi?  Check to see if your drive is still under warranty:

[http://www.hitachigst.com/portal/site/en/menuitem.4e6284c20a3050a7760062f6aac4f0a0/](http://www.hitachigst.com/portal/site/en/menuitem.4e6284c20a3050a7760062f6aac4f0a0/)

Thanks for the link! I've got 3 Hitachi drives being used on my server, one of which has "1" bad sector that was found and repaired. :D

I'll bookmark that link and RMA the drives if they get to the critical point.

---

### Post by az on 2009-10-24
> **CharlesA said:**
> Thanks for the link! I've got 3 Hitachi drives being used on my server, one of which has "1" bad sector that was found and repaired. :D

I'll bookmark that link and RMA the drives if they get to the critical point.

One bad block is no big deal.  That's normal and not a reason to RMA adrive.  I could not see the details on the screenshot so I just assumed it was a significant problem.  

Also, from Canada, I believe the warranty period on Hitachi drives is two years - that's not very much.

---

### Post by gtaluvit on 2009-10-24
I find it funny because it's reporting twice as many bad sectors as sectors on the HD! For the record, I just installed Karmic last night which is why I saw this issue. It's a Samsung HD, not Hitachi. It'll be interesting to see if they get this fixed prior to release because if this many people have seen it in the RC, the full release will be funny. Not good when a new install of an OS says "Your harddrive is about to die, you better buy a new one!"

---

### Post by P4man on 2009-10-24
[CENTER][SIZE="6"]Ubuntu 9.10[/SIZE]
[SIZE="4"]Sponsored by Hitachi, Seagate and Western Digital[/SIZE][/CENTER]

---

### Post by CharlesA on 2009-10-24
> **az said:**
> One bad block is no big deal.  That's normal and not a reason to RMA adrive.  I could not see the details on the screenshot so I just assumed it was a significant problem.  

Also, from Canada, I believe the warranty period on Hitachi drives is two years - that's not very much.

Yup I know. I just wanted it for future reference. :) I've got my RAID software set to notify me if/when the bad sectors reach a critical level.

---

### Post by arnab_das on 2009-10-25
am getting the same message. "bad sectors" etc. however i never got these messages when i was using windows or 9.04. is this really a bad sector error or is it a bug of ext4?

---

### Post by Tapas Bose, India on 2009-10-25
> **arnab_das said:**
> am getting the same message. "bad sectors" etc. however i never got these messages when i was using windows or 9.10. is this really a bad sector error or is it a bug of ext4?
Ha vaai eta bug. 
Yes this is a bug. I think.
See [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/438136)

---

### Post by arnab_das on 2009-10-25
wish i had stayed with ext3 and 9.04 :(

but the interface of karmic is simply toooooo good. firefox never looked this awesome and the human theme is simply amazing!

kudos to 9.10 for a job well done, but still have doubts about usability of ext4, if this is indeed a bug.

---

