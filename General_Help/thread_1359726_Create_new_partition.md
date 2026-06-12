---
title: "Create new partition"
date: 2009-12-20
forum: General Help
---

### Post by jamorod on 2009-12-20
I have purchased a Dell Vostro 1014 with Ubuntu. I just upgraded it to Ubuntu 9.04. And I am almost new to this.

Anyhow, I want to create a partition to keep my data related to my work in a separate place from the partition where all the program files and OS files are stored. I see there is already an OS partition, but I guess the rest of the program files are being installed in the "File System" partition.

For information:
jamorod@dell-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b592431

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         658     5242880    b  W95 FAT32
/dev/sda3   *         659       30153   236918587+  83  Linux
/dev/sda4           30154       30401     1992060    5  Extended
/dev/sda5           30154       30401     1992028+  82  Linux swap / Solaris
jamorod@dell-desktop:~$ 


I have a 250 GB HDD. In the file browser I get 2 partitions, one is called OS (5GB) and the other one is the File System (206GB).

I guess I will have to split the sda3 partition. How do I do that?

Thank you for your help in advance.

---

### Post by blackened on 2009-12-20
Is Ubuntu the only OS on this machine or is Windows installed as well? If Windows is installed, then you may have to muck around with GRUB after you change the partition arrangement.

Put in a live cd and fire up gparted. Make sure you have no other storage devices (USB sticks, SD cards) inserted so as to eliminate any possible confusion.

In gparted, you will need to shrink /dev/sda3 down to a more modest size (a.k.a. the amount of free space you want to end up with), then press "Apply" to complete the action. Wait for it to finish.

When that's done, you'll need to move both /dev/sda4 and /dev/sda5 to the left to fill the unallocated space you just created. "Apply" again.

The end result will look just the same as it did before, but with the unallocated space left at the end of the drive. From there you can create a new partition in the unallocated space and either mount it by hand or place an entry to it in /etc/fstab.

---

### Post by jamorod on 2009-12-20
Blackend, thank you for your quick reply.

No, there is no Windows in this machine... I'm trying to run away from Microsoft; I hope I manage.

Since Ubuntu came already with the computer, I don't have any CD but the one that I created from the recovery option given on the desktop. Should that be enough? I'll try it out as soon as I finish burning it... it is in the process right now.

---

### Post by jamorod on 2009-12-20
Ok, I´ve just realized of my silly question about the live CD. I´m already downloading the image for Gparted Live and burning it onto a CD.

---

### Post by jamorod on 2009-12-21
In the end, I did use the CD from the Dell Recovery CD, booted from there and used GParted from there.

I did all what blackend told, however, even if I have the unallocated area at the end, I cannot create the new partition out of it. It tells me:

"It is not possible to create more than 4 primary partitions. If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

I thought of including this unallocated area within sda4 which now is right after sda3 (and sda5 is part of sda4). But I'm not sure about how I should do that and if it is the best thing to do. Should I?

---

### Post by SecretCode on 2009-12-21
If the unallocated space is **after **sda4, the extended partition, you won't be able to use it - but if you extend sda4 to include it all then you'll be able to allocate many logical partitions within the extended partition.

What's your _fdisk -l_ at the moment?

---

### Post by john newbuntu on 2009-12-21
You will need to resize your extended partition /dev/sda4.  If you select the extended partition and right click resize, you can move the left arrow left to occupy the free space.  Once you commit this, you can then create a new filesystem (/dev/sda6) with that free space.  So eventually you would have the 2 logical partitions /dev/sda6 and /dev/sda5 under the extended partition /dev/sda4.  The rest are primary.

---

### Post by jamorod on 2009-12-21
Right now, my fdisk looks like this:

jamorod@dell-desktop:~$ sudo fdisk -l
[sudo] password for jamorod: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b592431

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         658     5242880    b  W95 FAT32
/dev/sda3   *         659       15052   115619805   83  Linux
/dev/sda4           15053       15300     1992060    5  Extended
/dev/sda5           15053       15300     1992028+  82  Linux swap / Solaris
jamorod@dell-desktop:~$ 

I'll try extending the sda4 and making a new logical partition within it. Let's see how it goes...

---

### Post by jamorod on 2009-12-21
I've created the new logical partition within sda4. My fdisk looks like this right now:

jamorod@dell-desktop:~$ sudo fdisk -l
[sudo] password for jamorod: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b592431

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         658     5242880    b  W95 FAT32
/dev/sda3   *         659       15052   115619805   83  Linux
/dev/sda4           15053       30401   123290842+   5  Extended
/dev/sda5           15053       15300     1992028+  82  Linux swap / Solaris
/dev/sda6           15301       30401   121298751   83  Linux
jamorod@dell-desktop:~$ 


However, I cannot do anything in that partition, at least not through the file browser. It seems I don't have the permissions to do so. How can I get those permissions?

---

### Post by SecretCode on 2009-12-21
I presume you created a filesystem on the new partition.

You still need to mount it.

Quick and dirty: if you go to the Places menu, you might find an entry for "113GB Media" (or whatever size it is). That should give you access.

Better:
```
sudo mkdir /mnt/sda6
sudo mount -t ext3 /dev/sda6 /mnt/sda6
```
(Assuming you formatted it as ext3)
And then browse to /mnt/sda6.

Even better:
Decide if you want to use this new partition as /home, or /home/yourname/Music, or some other predefined point in the filesystem hierarchy. Then you can edit /etc/fstab appropriately and move relevant files.

---

### Post by SecretCode on 2009-12-21
Or, assuming you've done all that but have permissions problems, ... you might need additional mount options.

---

### Post by jamorod on 2009-12-21
I have mounted the partition, but I skipped the step of creating the file system. How should I do that? Do I have to re-format that partition? I guess that at least unmount it, right?

I did format it as ext3.

The idea of re-locating the /home folder is great. I assume only my files will come, while the OS files will remain in the other partition. In the fstab folder, I only need to change the sda number? Which folders should I move then?

Am I asking too many questions? Thank you!

---

### Post by SecretCode on 2009-12-21
Formatting is the same as creating the filesystem, so that's done.

There are some good guides on the net to moving your files and updating /etc/fstab - for example:
[Partitioning/Home/Moving - Community Ubuntu Documentation](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[Create a separate home partition in Ubuntu](http://www.psychocats.net/ubuntu/separatehome)
[Move /home to it’s own partition « Ubuntu Blog](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by blackened on 2009-12-21
> **jamorod said:**
> The idea of re-locating the /home folder is great. I assume only my files will come, while the OS files will remain in the other partition. In the fstab folder, I only need to change the sda number? Which folders should I move then?

The linux directory structure is very rigid, but is very flexible in some useful ways, although it can be confusing coming from Window's willy-nilly put-anything-anywhere-you-want way of doing things.

The core structure is very important because the OS expects to be able to find key files in certain places and is not forgiving if it doesn't find what it's looking for. This is part of the reason that regular users do not, by default, have permission to modify files outside of their home directories.

Some of the flexibility is evident in the mounting system: you can mount almost any partition from almost any storage device in almost any part of the directory structure. 

As for moving your home directory to a new partition, start here (obviously skipping the parts about creating a new partition) -> [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome").

Good luck.

---

### Post by jamorod on 2009-12-21
I've spent quite some time yesterday trying to do it (moving home)... unsuccessfully and now I cannot even login to my account, but I will try again later on today when I get some time. I'm not sure of what exactly went wrong, but I think it may have been at the moment of copying files.

---

### Post by jamorod on 2009-12-22
Well it seems that the problem was that the line 

find . -depth -print0 | cpio --null --sparse -pvd /new/

should have been

sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

i.e. including sudo before the two commands. I had seen the errors earlier, but ignored them. Now things seem to be working, but I'm still on the process... I will confirm when I have finished.

---

### Post by jamorod on 2009-12-22
Now everything seems to be fine, only with the small "surprise" (to me, because I expected it otherwise), that in the file browser, only one partition is shown, within which the home folder is placed.

However, the free space of that partition shows to be 88 GB, while for the home folder appears as 106 GB. So, I assume the data is going into a different partition. I hope not being deceived!

In any case, thank you Blackend and Secretcode, you really helped me a lot!

---

### Post by blackened on 2009-12-23
> **jamorod said:**
> Now everything seems to be fine, only with the small "surprise" (to me, because I expected it otherwise), that in the file browser, only one partition is shown, within which the home folder is placed.

However, the free space of that partition shows to be 88 GB, while for the home folder appears as 106 GB. So, I assume the data is going into a different partition. I hope not being deceived!

In any case, thank you Blackend and Secretcode, you really helped me a lot!

Glad you got it working. Odd about the size difference, but unfortunately I have no explanation for it. What's df -h got to say about it?

---

### Post by jamorod on 2009-12-23
jamorod@dell-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             109G   15G   89G  15% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  124K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  200K  1.5G   1% /dev
tmpfs                 1.5G   88K  1.5G   1% /dev/shm
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda6             114G  2.1G  106G   2% /home


I think this is fine now, right?

---

### Post by blackened on 2009-12-24
```
Filesystem	Size	Used	Avail	Use%	Mounted on
/dev/sda3	109G	15G	89G	15%	/
tmpfs		1.5G	0	1.5G	0%	/lib/init/rw
varrun		1.5G	124K	1.5G	1%	/var/run
varlock		1.5G	0	1.5G	0%	/var/lock
udev		1.5G	200K	1.5G	1%	/dev
tmpfs		1.5G	88K 	1.5G 	1% 	/dev/shm
lrm 		1.5G 	2.2M 	1.5G 	1% 	/lib/modules/2.6.28-17-generic/volatile
/dev/sda6 	114G 	2.1G 	106G 	2% 	/home
```
Any time you post output from the terminal, please be kind enough to wrap it in code tags so that it will retain its original formatting. Makes reading it much easier and faster.

So what it looks like is that you now have a root partition (/) that is ~110GB, and a home partition (/home) of ~115GB. Technically there's nothing wrong with that, but many would tell you to shrink the root partition as it's just taking up space unnecessarily. 

Ideally, you shouldn't need more than 20-25GB max for your root partition. Everything else can go to either your home folder/partition or a separate data partition if you so choose.

Right now there is nothing functionally wrong with your setup that I can see though.

---

### Post by SuperSonic4 on 2009-12-24
> **jamorod said:**
> ```
jamorod@dell-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             109G   15G   89G  15% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  124K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  200K  1.5G   1% /dev
tmpfs                 1.5G   88K  1.5G   1% /dev/shm
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda6             114G  2.1G  106G   2% /home
```


I think this is fine now, right?

I see no problems with that. Perhaps / is a little big but if you have the room then why not? A large / will enable you to keep more of the old version of packages - useful for downgrading and saving bandwidth (as you don't have /var on a different partition)

---

### Post by jamorod on 2009-12-25
Sorry about the code tags... I don't fully know how to do it, but next time I have to post something I'll find out. Thank you anyhow.

---

### Post by blackened on 2009-12-27
> **jamorod said:**
> Sorry about the code tags... I don't fully know how to do it, but next time I have to post something I'll find out. Thank you anyhow.

No worries, live and learn. That's the fun of it all. You're very welcome.

---

