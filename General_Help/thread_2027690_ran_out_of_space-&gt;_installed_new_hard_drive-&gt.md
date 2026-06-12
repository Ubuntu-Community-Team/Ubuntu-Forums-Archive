---
title: "ran out of space-&gt; installed new hard drive-&gt; now what?"
date: 2012-07-16
forum: General Help
---

### Post by PineappleCore on 2012-07-16
I installed ubuntu a few months ago and love it. I didn't have a lot of space to begin with but now I can't update it or get the new release because there isn't enough space on the drive. So I got a wiped drive from another computer and put it in. 

Should I uninstall ubuntu on my original hard drive? is it worth the time to do it? It doesn't have a large partition.

or 

Should I keep it there and install the system on the new drive? How do I do that? 

What else should I be aware of?

---

### Post by papibe on 2012-07-16
Hi PineappleCore. Welcome to the forums! ):P

It all depends on how did you install Ubuntu. Did you use Wubi or did you installed it using one of the ISO CD/USB?

Regards.

---

### Post by OM55 on 2012-07-16
This reply is valid in case you installed Ubuntu from the ISO (not with Wubi).

If the new hard drive is smaller than the existing drive (where Ubuntu is currently installed) you can simply mount the new drive under your home folder (or another location, based on what you want to do). This in effect will be seen from your point of view as a user as having a directory on the original drive that has a space capacity of the entire new hard drive. Then you can transfer to this folder what ever you want from the original drive, clearing some space on it.

The mounting should be done in the /etc/fstab so you be persistent between boots.

If you new hard drive is larger than the existing drive (where Ubuntu is currently installed) it would make more sense to transfer the Ubuntu installation to that larger drive, or simply install a fresh install on the new drive.
Fresh install will allow you to start from scratch but at the same time may take some time to restore and set up all the things to your liking.

If you prefer to close the existing installation to the new hard drive, you can do that with Image for Linux ([http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm)). With Image for Linux (IFL) you can create an image backup of your entire old hard drive, then restore it to the new drive and allow it to expend the size of the partition to the available size on the disk.
When done, you can mount the old (smaller) drive as an additional available disk space on your new drive (just like I described before).

Hope that helps.

---

### Post by PineappleCore on 2012-07-17
Thanks for your reply! I didn't know you could mount a hard drive inside  a folder that is pretty cool. I think I am going to have to uninstall  ubuntu my original drive is 30G and my "new" one is 80G. 

I am a little intimidated by the task at hand but if I mess it up not a  huge deal; this machine is 10 years old. Non-the-less I'd rather set it  up right for another 10 years!

---

### Post by OM55 on 2012-07-17
As long as you don't touch or make any changes to the old drive you should be fine. Just image backup the old drive, replace drives and restore to the new drive. This way if there is any problem, just put back the old drive in the laptop and restart - you should be back to the current status.

As for mounting a hard drive, you can do that using the 'mount' command (this would last only until the next log off):

```
mount <device name> <mount point>
```In the following example the drive partition /dev/sda2 was mounted to the folder /home/david/newdrive. You have to make sure that the destination folder exists:

```

mkdir /home/david/newdrive
mount /dev/sda2 /home/david/newdrive

```so now the folder /home/david/newdrive IS the entire drive partition /dev/sda2

To make the mounting in this example persistent between reboots, edit (CAREFULY) the file /etc/fstab to add the line:

```
/dev/sda2       /home/david/newdive  ntfs  0  0
```Of course, change the 'ntfs' in the line to the correct method.
You can find more info about how to edit the content of /etc/fstab at: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Hope that helps.

---

### Post by gordintoronto on 2012-07-17
As a temporary meansure, you might run a terminal and enter this command:
sudo apt-get clean

And if you really want to extend the life of an old computer, you should consider Lubuntu or Xubuntu.

---

### Post by PineappleCore on 2012-07-18
So in review (correct me if I am wrong) if i want to be able to upgrade ubuntu using the space on the new drive I could mount the drive in the home folder. 

Will that work if I am going to need the space for system files?

---

### Post by OM55 on 2012-07-18
The system will not use anything out of the initial partition for system files. So no matter where you mount the additional drive, the system will not use it. It will be for your files.

---

