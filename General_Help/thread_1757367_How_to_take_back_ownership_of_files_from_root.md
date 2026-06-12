---
title: "How to take back ownership of files from root?"
date: 2011-05-13
forum: General Help
---

### Post by ron177 on 2011-05-13
How can I change ownership of my external hard drive? Right now, everything I have in my hd has not be modified only when I am signed in as root. How can I take back the ownership?

---

### Post by gradinaruvasile on 2011-05-13
Mount the drive as user or chmod 777 the mountpoint.
And chown back the files already written:

cd to mountpoint and 

sudo chown username . -R

username-your user name.

---

### Post by ron177 on 2011-05-13
So I followed the steps you outlined. But unfortunately I wasn't able to change permission. 



I also read a little about this online and typed in the following command in the Terminal:



chown -Rv [my username] /dev/sdc 

The response I got from the system was:
 

changed ownership of `/dev/sdc' to [my username]
 

But the problem persists. I still do not have permission to edit and  save files on my hard drive (/dev/sdc). I can only view them and read  them. Is there anyway someone can help me with this?


 Appreciatively!

---

### Post by gradinaruvasile on 2011-05-13
> **ron177 said:**
> So I followed the steps you outlined. But unfortunately I wasn't able to change permission. 



I also read a little about this online and typed in the following command in the Terminal:



chown -Rv [my username] /dev/sdc 

The response I got from the system was:
 

changed ownership of `/dev/sdc' to [my username]
 

But the problem persists. I still do not have permission to edit and  save files on my hard drive (/dev/sdc). I can only view them and read  them. Is there anyway someone can help me with this?


 Appreciatively!


Nooooo. I meant MOUNTPOINT, not DEVICE.

The device has to be owned by root and the disk group. The restricted user has no business there.
Do this in a terminal:

sudo chown root:disk /dev/sdc

Mountpoint is the folder where the device (/dev/sdX) is mounted. That is not a pre-defined one like in windows c/d/e/etc, but generally it is under the /media/ folder (except for the root partition).

You can find it like this:

mount | grep /dev/sdc

You will ge something like this (this is from my computer, i have other device names, adjust them accordingly):

/dev/sdb1 on /media/bad-data type ext4 (rw,relatime,commit=0)
/dev/sdb2 on /media/small-bad-data type ext4 (rw,relatime,commit=0)

Notice the numbers - those are the partitions on the /dev/sdb device (my second hard disk used for storage).
So, the first partition of the /dev/sdb drive is mounted in the /media/bad-data folder. Yours will be different, most likely a long string if you havent assigned a label to it.
You have to chown that folder in which /dev/sdbX is mounted. I dont know X because you might have more than 1 partitions, if you have 1, then it is /dev/sdb1

---

