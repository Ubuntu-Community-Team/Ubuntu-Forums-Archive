---
title: "How to create /home partition when installing Ubuntu?"
date: 2012-01-29
forum: General Help
---

### Post by Stovey on 2012-01-29
Would someone please walk me through partitioning during installation?

I have tried several times to use the partition manager provided by the GUI, but it seems to give me errors.  ie one of my partitions had no space!  I would like to set up a separate partition for /home, but I don't know how.

I suppose I should also create a swap partition. So there would be 3 partitions ie swap 4 GB, / 8GB, and /home the remainder.

Would someone explain how to do this, simply and clearly?  Thanks!

---

### Post by oldfred on 2012-01-29
Are you partitioning as part of the install or before? I usually partition in advance and use manual install or Something else to choose which partition is / (root), /home & swap.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

But the installer is not a lot different. Have you used all 4 primary partitions?

May be best to post a screen shot from gparted. Use the Ubuntu liveCD or download a separate liveCD with gparted. Thne we can give more specific suggestions. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by nipunshakya on 2012-01-29
Go with **oldfred  **with this....both his links are clearly understandable. Before going to your partition scheme, its better to let us know how your current partitions are, so that we can help you out with best on how u can manage your partitions. If you have 4gib ram on your machine, you may not require a swap area(depends on you). Rest, the / requires 10-15 gib and /home as rest of your machine's space.Goodluck.

Regards,WinuxUser

---

### Post by Stovey on 2012-01-29
Hi Fred!  Thank-you for your quick response.

I was trying to partition during a fresh install, wiping everything clean.  I am hearing you say that it is better to partition in advance.  If I understand this correctly, I can partition, save my existing home directory, and then install the new system?

I have 3.8 GiB RAM, so I guess swap is unneccessary.  But I also have a 320 GB harddrive, and really only use 1/10th of that.  So a swap partition isn't going to be a hardship - I have plenty of space.  I am not interested in dual-booting.  

I will take a few moments to read the Gparted tutorial, and then I will report back with screen shots.

Many thanks.

---

### Post by nipunshakya on 2012-01-29
well 320 gib really means similar to mine....:D
Regarding the partitions, well u got 4 gib ram, so no requirement to allocate swap. However, u can partition 2gib of it as swap(just in case).
Then you can have a 15-20 gib of / and then rest of it as /home.... That would help you....

Regards,WinuxUser

---

### Post by Stovey on 2012-01-29
Hi everyone!  Thanks Fred for the AWESOME tutorial.  Now, I *think* I know what I'm doing.

1. Load GParted in LiveCD.
2. Resize the system partition sda1 to 16 GiB.
3. Resize the extended partition sda2 to the remainder.
4. Add a logical partition for /home to the extended partition.  Make the mountpoint /home on this partition.

Screenshot:  [Existing system in GParted](http://i128.photobucket.com/albums/p195/BassBucket/GParted_Me_20120129.png)

Am I on the right track here?  What do I need to do when it comes time to install Ubuntu 12.04? I guess I will have to specify partitions manually.

I notice GB changed to GiB when I wasn't looking - I was totally unaware of this till now.

---

### Post by oldfred on 2012-01-29
Looks fine, I would put a swap in the extended also, if you are creating one. I normally suggest something for swap, but many with lots of memory many say its not used. Others do video editing and never have enough memory, and some say it boots slightly faster with swap as it has to discover there is no swap first. 

Since you can have only 4 primary and the extended is one of the primary, I do like to have most of my partitions in the extended as logicals. Windows and a very few others require primary partitions, so saving one or two is worthwhile if later you need one.

When you use manual install, you choose your partitions, which format and which is /, & /home. If reinstalling you do have to be careful to choose /home but specify not to reformat. If you have lots of room I like a separate / for a new clean install. I have / on three different dirves and rotate them as which is my current working. Now with a new SSD I will just have two / on the SSD and rotate back & forth.

---

### Post by Stovey on 2012-01-29
Okay, here is what my drive looks like now:

[New partitions](http://i128.photobucket.com/albums/p195/BassBucket/NewSystem_GParted.png)

I think this looks good!

I have one question left.  How do I move my home directory into the new partition sda6?  sda1 mounted automatically as root, but I don't really see how to mount sda6 as /home.

---

### Post by nipunshakya on 2012-01-29
Boot to livecd, right click on /sda6,select create new partition, under the mount point, use it as /home and apply changes....u might want to read the following:

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

also see the screenshot to know what i meant...in example, it is mounted as /boot...change it to /home okay....goodluck.

Regards,WinuxUser

---

### Post by Stovey on 2012-01-30
Thanks Winux.  When I created the sda6 partition, GParted didn't give me any options for specifying a mount point.

Are you saying that when I re-install Ubuntu, I will specify sda6 as /home, and Ubuntu will automatically move my home directory over?  (From the yellow bar, it already looks like data is in sda6, even though it's brand new).

---

### Post by oldfred on 2012-01-30
If you have data or settings in your current home you need to back that up and copy it to your sda6 partition.

A new clean install of Ubuntu does not save anything except when you have all your data in a separate /home AND tell it not to reformat that separate /home partition.

If you want to move data or settings to your sda6, you can do the first part of the instructions of moving /home. Since you are reinstalling you do not have to do most of it. You have already created partition and should just have to mount it and copy all the data over.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Stovey on 2012-01-30
Thank-you Fred and Winux for your assistance!

---

### Post by nipunshakya on 2012-01-31
Glad to be at your service man...

Happy Linuxing
Regards,WinuxUser

---

