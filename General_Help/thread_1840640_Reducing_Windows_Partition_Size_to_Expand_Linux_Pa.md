---
title: "Reducing Windows Partition Size to Expand Linux Partition Size"
date: 2011-09-07
forum: General Help
---

### Post by LinuxFanBoi on 2011-09-07
So it seems I underestimated the amount of partition space I would need when I installed Ubuntu.  I Originaly allocated 50 GB thinking that would be enough, but I'm now getting warnings that tell me I have about 1.5 GB left.

Using windows, I shrank my windows partition and now have 50 GB of unalocated space on my HDD that I would like to use to expand my Linux partition.  I tried to run 'gparted' from Ubuntu live that still resides on the USB drive that I used for the install, but it wont let me just expand the existing Linux partition to consume the unalocated space I've set aside.

I don't want to do a complete re-install, I just want to give the unalocated space to my current linux partition. What do I do?

---

### Post by papibe on 2011-09-07
If your Windows partition is on the beginning of the disk, then you may try to fist move your Ubuntu partition to the left to close the gap created by reducing your Windows partitions. Once it's moved, you can expand it to the right.

Does that make sense to you?

Hope it helps,
Regards.

P.D.: Don't forget to backup your data ;-)

---

### Post by oldfred on 2011-09-07
Do you have /home inside your root partition? I typically recommend a / of 10-20GB and that should normally use only 6-7GB with lots of programs. It is usually your data that takes up lots of room. Systems both Windows & Ubuntu are somewhat better with smaller system partitions and larger data partitions.

If dual booting with Windows do you also have a separate shared NTFS partition for any data you may want in both systems? I have my Firefox & Thunderbird profiles in the NTFS shared partition even though I now use XP very little.

Post screenshot from gparted.

---

### Post by nipunshakya on 2011-09-08
It seems that you have a dual boot for your machine. . .if you could kindly show what your partitions look like, there might be a solution for that too....
please note that your windows can have only 4 primary partitions (excluding unallocated space ofcourse)in it...and so if you have tried to create this **might** be one reason why your gparted isn't being able to use your unallocated space...still i found a similar problem's solution and it looke like this (see the link and check if your problem is alike)
[http://ubuntuforums.org/showthread.php?t=1741636](http://ubuntuforums.org/showthread.php?t=1741636)

Goodluck.
Regards,WinuxUser

---

### Post by LinuxFanBoi on 2011-09-08
> **WinuxUser said:**
> It seems that you have a dual boot for your machine. . .if you could kindly show what your partitions look like, there might be a solution for that too....


here you go...
[IMG]http://img202.imageshack.us/img202/2311/screenshotdevsdagpartedr.png[/IMG]

---

### Post by LinuxFanBoi on 2011-09-08
problem solved...  I setup a USB flash drive to boot the system into Gparted Live which is a minimal Linux installation.  With that I moved /dev/sda4 to the left to put the unalocated space to it's right.  Then re-sized /dev/sda5 to consume the unalocated space to it right.

Now here comes the "duh" moment.  You can't move empty space,  but you can move something into that empty space.

here's what my system looks like now..
[IMG]http://img714.imageshack.us/img714/192/screenshot320gbharddisk.png[/IMG]

---

### Post by nipunshakya on 2011-09-08
^^^ thats great....looks like it will work for you now...goodluck

---

### Post by checoimg on 2011-11-29
So you just made a new partition and named it like the one with the Ubuntu installation to cut and paste the whole Ubuntu installation ?

---

