---
title: "Cant Boot!!! Help Please"
date: 2006-02-25
forum: General Help
---

### Post by Royal2000H on 2006-02-25
Ok So I'm using a dual boot between Windows and kubuntu....

I had Windows first, then installed kubuntu, so when making partitions, I gave Windows more room....

After a long time using only kubuntu, I decided to take out 45 GB from the Windows, and into the linux...

So I erased lots of unneeded files in Windows, then used Paragon Partition Manager to make free space from the windows and add it to the linux...

So i rebooted (because it cant do it with Windows running)...and it took a looong time to set up (longer than usual)....

I go into Linux, and I still only have 8 GB free space, What About that 45 GB?!?!

I boot back into Windows and open up Partition Manager

Now it shows those 45 GB of space as *used* ext3....but it should be free ext3 how did it become used??

So i go back into linux to see if i can do anything about it....and I cant.....so I go back into Windows....

And it was late night so I got really tired and went to sleep;

The next day I wake up nd look at the screen, and it's just black; I move the mouse and click (and say to myself ugh windows) and then press the power button and then I realize it's linux say cant open or something "/sbin/getty"

and I cant do anything about it....
I press and hold power button, boot into linux again, same thing, I boot into recovery mode, same thing, I boot into windows and it say "updates were installed (so thats why it rebooted, and linux is default, so thats how it got to linux)



In short:
I cant boot into kubuntu, it says something about "/sbin/getty"
I am posting from the same box, but Windows...

---

### Post by Royal2000H on 2006-02-25
OK well I figured half of it out.....


The reason it ran in the beginning but then didnt run later is because I (stupidly) mounted my windows partition (as an ext3) to / (so there I had two mounted as /) thinking it was the free missing space.....

In windows I used Paragon Partition Explorer to edit /etc/fstab to remove that mount.....

And now I'm in....

But still I have that problem of ~45GB that disappeared into thin air.....

Looking closer into details "Disks & Filesystems" shows 68.5 (I think the addition of the ~45 GB made it that size)

BUT Partitions in KInfoCenter shows 24,753 MB (I think pre-addition)


Like I said in my previous post.... Paragon Partition Manager claimed the ~45GB was used..... thought it should be free....

Any Ideas Please?

---

### Post by aysiu on 2006-02-25
There may be a fix for this, but I don't know it.
Your best bet is to reinstall.
I would do it in these steps:

1. Using a live CD and some kind of external media (iPod, blank CDs, whatever), back up all the important documents on the Ubuntu installation. Knoppix is ideal for this, but you can use the Ubuntu Live, too--you'll just have to do some extra steps to get the partition mounted.

2. Using that same live CD, use and/or install QTParted or GParted and delete all Ext3 partitions and then create one huge one (or keep it as is and use the 45 GB one as /home partition and the other as / partition). That way if you ever have to reinstall again, it'll be a lot less painful.

3. Use the Ubuntu CD to install on to the new partition(s).

P.S. I've no experience with Partition Magic, but I've read several times that it doesn't do so well with Ext3. I'd use a Linux partitioning program instead.

---

### Post by Royal2000H on 2006-02-25
[QUOTE=aysiu]There may be a fix for this, but I don't know it.
Your best bet is to reinstall.
I would do it in these steps:

1. Using a live CD and some kind of external media (iPod, blank CDs, whatever), back up all the important documents on the Ubuntu installation. Knoppix is ideal for this, but you can use the Ubuntu Live, too--you'll just have to do some extra steps to get the partition mounted.

2. Using that same live CD, use and/or install QTParted or GParted and delete all Ext3 partitions and then create one huge one (or keep it as is and use the 45 GB one as /home partition and the other as / partition). That way if you ever have to reinstall again, it'll be a lot less painful.

3. Use the Ubuntu CD to install on to the new partition(s).

P.S. I've no experience with Partition Magic, but I've read several times that it doesn't do so well with Ext3. I'd use a Linux partitioning program instead.[/QUOTE]
Is this post pre-reading my second post...or after?


Also here's a screenshot of my file space notice the "of 24.2" and "size 46.5"

I'm thinking somehow some data was transfered over from the files of windows (because I deleted those files just minutes before partitioning (and I think I didn't clear the recycle bin so they were temporarily there or something)

---

