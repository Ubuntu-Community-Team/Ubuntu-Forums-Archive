---
title: "Auto Mount SoftwareRAID in Karmic"
date: 2009-11-03
forum: General Help
---

### Post by sux2bu101 on 2009-11-03
Ok...  First off, I am fairly new to the Ubuntu Community, started using it about 6 months ago.  I've found my way through a lot of the little issues I had thanks to this forum.  Thank you.

Now to a question I have not seen the answer.  I put togeter a simple home PC, with the intention of keeping a redundant copy of all the pictures and other misc data that my wife and I have accumulated over the past few years.

So here is what I wanted, OS (Ubuntu) on one HD and all data on a RAID 1 array. So a total of 3 discs, one for OS and the other for data.  I would like the OS on a seperate disk, incase I mess up something and need to do a fresh install.

For the most part I have this.  I am also very new to RAID arrays.  I ended up doing a SoftwareRAID using the Karmic Disc Utility.  Which for a new user to RAID arrays was pretty easy.  However, I have one small annoyance.

When I bootup the system, I cannot figure out a way to automatically mount the RAID array.  Here is why...  Before I can mount the RAID, I have to first manually start it in the Disk Utility, THEN I can mount it.

Is there away to automatically start the SoftwareRAID array and mount it during the login process?

Any suggestions?

---

### Post by brynr on 2009-11-07
I was also having this issue, except I have a RAID 5 array

I was following [this guide]("http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/") for manually creating a raid array (through terminal using mdadm) until I discovered the disk utility way...
However the guide has steps for getting the array to auto mount and these seemed to work for me (with a bit of tweaking)


First make sure the array is started with disk utility

Then in terminal:
```
sudo cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.old
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```If you get a message like *bash: /etc/mdadm/mdadm.conf: Permission denied* then use root terminal. This is available under Applications -> System Tools (and you may have to edit the menus to have it show up!)

Now at this point I discovered that the above step will not produce the right entry in your mdadm.conf if you have a space in the array name! if you have a space like I did, just edit the line created by mdadm --detail --scan so that the Name is in quote marks. this fixed things up for me!

Now create a directory to automount to
```
sudo mkdir /media/data
```Now edit the fstab file which mounts drives at startup
```
sudo nano /etc/fstab
```and add a line for the raid array. I used [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) to help me and the line I added in the end looks like the following, your's will probably be different!
```
/dev/md0    /media/data    ext4    rw,user,auto    0    3
```
Hope that helps you sort things out![URL="http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/"]
[/URL]

---

### Post by laluz on 2009-11-08
First of all, RAID is no backup solution. A driver bug or a power outage may corrupt your data on both (all) raid drives. 
To get the raid mounted theoretically all you need is a record in the /etc/fstab
/dev/md0 /media/RAID jfs rw,nosuid,nodev,uhelper=hal 0 0 
I just happen to be on 8.10 where hal is still in use and my filesystem is jfs. So you will need to change a few things.
And practically also check this thread [http://ubuntuforums.org/showthread.php?t=992559#9](http://ubuntuforums.org/showthread.php?t=992559#9)
 to make sure this is not the problem you are still having in 9.10

---

