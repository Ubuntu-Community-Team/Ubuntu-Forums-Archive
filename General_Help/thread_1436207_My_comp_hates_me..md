---
title: "My comp hates me."
date: 2010-03-22
forum: General Help
---

### Post by TheJew on 2010-03-22
I have come to the conclusion that my laptop doesn't like me. Or anyone, for that matter. Windows screwed up royally on it, so my bf put Ubuntu on it. Tada! Less than two weeks later, it winds up with a worm, a couple trojans, and we're not sure what else. The system now will not boot. Period. It gets to the GRUB LOADING screen and then says something about no partition found or something. I'm not sure. He's in another town right now with the comp and trying to get help via phone to fix it. I know I'm horrible at describing comp problems, but I'm hoping I made some sense. Any ideas?

---

### Post by cbecker78 on 2010-03-22
I'm somewhat new at all of this, but it seems unlikely you acquired a damaging virus/worm while using ubuntu that is somehow affecting your ability to boot into Linux...But I don't really know.  There may be another reason.  a few questions:

How do you know you have a trojan/worm/virus?
were you still working in windows when you got this virus?
How old is your laptop?

It does seem likely that you have a damaged/partially-corrupted hard drive.  To see if a hard drive malfunction is causing a problem, boot from the CD you used to install Ubuntu.  Once booted to the CD, see if it will mount/load your hard drive and if you are able to browse files there.  Then report back.  (it may be a good idea to transfer/backup any really important files to a USB flash drive if you are able to browse your hard drive)

Some more experienced users may have some better advice, but you can't really hurt anything by booting from the CD, just don't install the OS from the CD if you have any information on the disk you want to hang onto...)

---

### Post by moshansky on 2010-03-22
Is windows still on the PC? That grub error message means it can't find the data to boot the operating system from (Windows or Ubuntu) If you haven't changed grub at all it's possible that their is a problem with the hard drive or simply the file system on that partition. Any more information you can provide would really help regarding the harddrive (eg. Partition layout)

---

### Post by davbren on 2010-03-22
What I would suggest for a quick and easy fix is to put the Ubuntu CD in and restart th epc. Use the live cd to backup ur files and do a clean install. 

It is *extremely* unlikely that you have a virus or worm etc. Not impossible, but I very much doubt thats the issue. But then, I do try the lottery on worse odds every week :D 

Although if Windows foobarred and now Ubuntu, it sounds like it could be a hardware issue. Possibly the harddrive itself. Which isn't really fixable by us.

---

