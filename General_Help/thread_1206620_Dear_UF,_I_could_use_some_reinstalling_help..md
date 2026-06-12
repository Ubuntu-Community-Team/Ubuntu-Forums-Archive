---
title: "Dear UF, I could use some reinstalling help."
date: 2009-07-07
forum: General Help
---

### Post by lariosa42 on 2009-07-07
Recently I installed Ubuntu 9.04.  To make a long story short, I tried to do something clever, but ended up with major permissions problems.

I want to do a full reinstall.  The problem is that I am in a remote location for research this the summer, and I have no access to blank CDs, etc.  I do have 4GB thumb drive.  My plan so far is to somehow get the thumb drive to work like a live CD (will USB Startup Creator do this?).  Next, I want to preserve my /home directory on a separate partition, and reinstall 9.04 with the "live thumb drive."

A major problem is that my harddrive is 120 GB, and my /home directory is about 100 GB.  Also, my drive is not partitioned yet (i.e., there is one single partition for everything).

Does anyone have a suggestion?  If the above plan is going to work, I'll need to find out how to:

1) Partition my drive when it's not already partitioned, without erasing my data.

2) Move my rather large /home directory to the new partition (maybe I could do this bit by bit, resizing as I go).

3) Get my thumb drive to work like a live CD (i.e., be able to install a fresh copy of Ubuntu).

Any help, suggestions, or reality checks would be welcome!

---

### Post by Legace on 2009-07-07
How much are you using of the 100GB /home directory?

---

### Post by lariosa42 on 2009-07-07
I'm not *actively* using much of it on a day to day basis, but I need essentially all of the data...

---

### Post by Legace on 2009-07-08
> **lariosa42 said:**
> I'm not *actively* using much of it on a day to day basis, but I need essentially all of the data...

You didn't answer my question..

---

### Post by Bucky Ball on 2009-07-08
Yea, in that case you want to shrink the partition, right? You probably have 30Gb of data you want to keep on a 100Gb partition or something along those lines?

---

### Post by lariosa42 on 2009-07-09
Legacy - 
Your question didn't really make sense.  I am of course using 100GB of my 100GB /home directory.  That's not the allocated space, that's the total amount of data I have.  My hard drive is about 120GB, as mentioned above.

Anyway, it doesn't matter anymore.  I was able to do it!  Luckily, I *was* able to find a blank CD! =)  Next, I partitioned my hard drive using [this]("http://www.psychocats.net/ubuntu/separatehome") excellent guide.  I made a small partition, moved some files over, resized the partition, moved more files, and so on.  Each resize took about an hour, so the whole process took all day.  Finally, I used the same guide to reassign my /home directory (I did have to use [FONT="Courier New"]sudo[/FONT] with the [FONT="Courier New"]find[/FONT] and [FONT="Courier New"]cpio[/FONT], and I also had to go into recovery mode and use [FONT="Courier New"]chmod[/FONT] and [FONT="Courier New"]chown[/FONT] as described in the guide).

Now all I have to do is reinstall Ubuntu.  Whew!

Thanks for your comments everyone!

---

### Post by Fixman on 2009-07-09
I recommend [Unetbootin]("http://unetbootin.sourceforge.net/") for having a Live-USB on ubuntu, and also you could try the last version (9.04).

Anyway, inside the Live USB you can delete all files on your partition except for your home (so the partition will occupy 100GB), shrink it down to 100GB, and install Ubuntu on the free space of your 120GB hard drive.

Then, when you install Ubuntu, you set the 100GB partition as your /home partition.

---

### Post by Bucky Ball on 2009-07-09
You are a patient Ubuntu-er, but the effort sounds worthwhile. Nice to hear it worked out.

---

