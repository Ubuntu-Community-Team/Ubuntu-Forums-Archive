---
title: "Failed to resize a partition correctly!"
date: 2010-10-03
forum: General Help
---

### Post by JshPuppy on 2010-10-03
Okay, yesterday I was moping around about how Jolicloud wasn't working for me, so I decided to just get rid of UNR on my netbook completely, and stick with Jolicloud (I'm starting to regret that though...).

Well, I've done about the most stupid thing that anybody could possibly do. I tried to resize a partition incompletely! Now, every time I boot it up, all I see is:

---
error: unknown filesystem
grub rescue >
---

It's a good thing I have both Ubuntu 10.04 Desktop Version on my SD card and a backup disk (Carbonite copy of all factory defaults. [http://www.carbonite.com](http://www.carbonite.com)). I also have an external CD drive for my broken netbook.

HOWEVER, with these tools, I cannot seem to bring my netbook back! I HAVE re-installed Windows, (all of my files lost, but thank god that I could boot from my Ubuntu SD card to retrieve my personal files :))

I also have tried GParted live USB. No luck there... It won't boot up.

Help! Is there a way to cleanly format (with partitions) my hard drive to a complete factory-default settings?

---

### Post by JLGreen on 2010-10-03
Are you trying to completely reformat your drive?  If you could provide more details of your system and what your hoping to accomplish, you'll probably get help faster.

---

### Post by JshPuppy on 2010-10-04
Alright, I'm trying to format my Acer Aspire One HD (160 GB) to only one partition, with all data cleared.

---

### Post by JLGreen on 2010-10-04
Can you boot off the Ubuntu that you have on your SD card or perhaps a USB drive?  If so have you tried using the disk format utility?  You might want to read over some of the options at the link below for help with installation.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by JshPuppy on 2010-10-05
[SIZE="1"]Hm, I'm not quite sure on what you mean there... Disk format utility? Sometimes when I boot up from Ubuntu, I can't launch certain programs (I get an input/output error). I can't even get a terminal up! But please elaborate on this disk format utility... (For I think I've tried to format the hard drive before with the built in Disk Utility... But it didn't work. Something about the daemon...)[/SIZE]

WELL, as it turns out, while I was in the middle of typing this post, I managed to be able to rid of all the partitions (using gParted on Ubuntu)! I then used gParted again (On Ubuntu again) to reformat my hard drive to ntfs type (my default), and then I took out my Carbonite Backup disk, and it's restoring Windows right now (Hopefully)! Woot.

For now, I have my problem solved. BUT, if it still wont work, I'll have to post again....

---

### Post by JLGreen on 2010-10-07
Glad to here you got something to work, please be sure to mark the thread as solved if it is.  You could also put the details of what you did with gParted so that others can learn from your experience.

---

