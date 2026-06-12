---
title: "Merge partitions and Backup"
date: 2011-09-05
forum: General Help
---

### Post by al1x on 2011-09-05
[LEFT]Hello, I'am running a dual-boot system, with winxp and ubuntu and I would like to know how can I merge an existing partition to the main one of the ubuntu or use it to store my home folder in order to upgrade ubuntu without moving my files.The selected partition is the one with the label "vegapunk".[/LEFT]


[IMG]http://ubuntuone.com/p/1FMA/[/IMG]

---

### Post by al1x on 2011-09-07
Any help please?:popcorn:

---

### Post by TBABill on 2011-09-07
If you know (for absolute certain) one of those partitions is either not used or not needed, you can simply select it and tell gparted to delete it. The space will remain but it will have no formatting assigned to it and will appear as unallocated space. You can then go to your root (/) partition, which for you is /dev/sda7, and increase its size using that unused space.
 
A couple important notes. You can't do it from a booted system. You'll need to do it from the liveCD or liveDVD so you do not have the partition mounted that you are growing (/). Also, you have many paritions and some of them are propbably recovery partitions for windows. Without knowing what's on each, it will be imperative for you to know with absolute certainty that you want to delete a partition before committing to it. And make sure you have Windows XP reinstall disks or you could find yourself without a copy of Windows if you bork something. Trust me, I've done it and felt the pain after realizing I never made backup disks.

---

### Post by btindie on 2011-09-07
Firstly, you can't modify a live partition so you'll need a recovery disk of some flavour. Your best bet for this is one called [Parted Magic]("http://partedmagic.com"). Put that onto a CD or USB disk and boot into it.

I'm assuming that you're on about 'merging' sda7 with sda8 ?

You can't merge partition especially when they're of different filesystems but you can resize/move them to create the same outcome.

So to 'merge' the two partitions you'd need to do the following:

[LIST=1]
[*]Resize sda8 to its minimum size, about 8GiB
[*]Move sda8 to the right, this will create a gap between sda7 and sda8
[*]Resize sda7 to use up all the free space to the right
[*]Mount sda7 and sda8 and then copy then contents of sda8 to sda7, then unmount both
[*]Delete sda8
[*]Resize sda7 to fill the empty space
[/LIST]

---

### Post by YesWeCan on 2011-09-07
You also asked about putting /home in sda8. More tricky but ok.
Messing with partitions is dangerous. Back up any vital data in /home and in sda8 before you start.

Using live CD/USB:
use GParted to reformat sda8 to ext4 **assuming you don't wish to keep the data in sda8 or you have backed it up somewhere.**

mount both the Ubuntu root and sda8
```
sudo mkdir /mnt/root /mnt/home
sudo mount /dev/sda7 /mnt/root
sudo mount /dev/sda8 /mnt/home

sudo rsync -vax /mnt/root/home/ /mnt/home/
```

Now edit the fstab file so /dev/sda8 is mounted at /home

Back it up first
```
sudo cp /mnt/root/etc/fstab /mnt/root/etc/fstab.bak
```

find out what the UUID (unique partition identifier) is for sda8
```
sudo blkid
```
Edit the fstab file
```
sudo gedit /mnt/root/etc/fstab
```
and add a line to mount the new home partition at /home, something like (use the correct uuid for sda8 ):
```
UUID=824f4788-8258-44cc-8efb-f1fc54b0fba7   /home   ext4   defaults   0   2
```

Reboot Ubuntu in sda7 and run mount to verify where /home is mounted:
```
mount
```

Make sure everything is present and correct in your home directory.


Your original files are still in sda7 but they are not being used anymore so you can delete them if, say, you want to make more space on sda7 or shrink sda7.

To do this you need to boot from live CD/USB and mount sda7:
```
sudo mount /dev/sda7 /mnt
```
and then delete the contents of the original home directory at /mnt/home.

---

### Post by al1x on 2011-09-07
> I'm assuming that you're on about 'merging' sda7 with sda8 ?
Yep.

> Resize sda8 to its minimum size, about 8GiB
Move sda8 to the right, this will create a gap between sda7 and sda8
Resize sda7 to use up all the free space to the right
Mount sda7 and sda8 and then copy then contents of sda8 to sda7, then unmount both
Delete sda8
Resize sda7 to fill the empty space


Why do all this instead of deleting the partition sda8 instantly and resize sda7 to give it the unallocated space as TBABill said?Also, do I have to reformat sda8 to ext4 before resizing sda7?

---

### Post by al1x on 2011-09-07
> You also asked about putting /home in sda8. More tricky but ok.

I'am not sure, is it better to merge the two partitions or move /home to sda8? Dedicating 15GB just to the filesystem is it ok?I think they're too much for a 160GB HD.
:roll:

---

### Post by nipunshakya on 2011-09-07
> **al1x said:**
> ...... Dedicating 15GB just to the filesystem is it ok?I think they're too much for a 160GB HD.
:roll:


I think that should work for you...:)

---

### Post by btindie on 2011-09-07
> **al1x said:**
> 
Why do all this instead of deleting the partition sda8 instantly and resize sda7 to give it the unallocated space as TBABill said?Also, do I have to reformat sda8 to ext4 before resizing sda7?
If you don't care about the 7.95GiB worth of data on sda8 then go ahead and simply delete the partition and resize sda7 to fill the available free space. I thought you wanted to preserve it.

Making one large partition will be much easier to do instead of creating a dedicated /home where you have to move the contents of the existing home and update some system files. But if you feel comfortable... plus if one partition fills up you can't easily use the available space on the other partition unlike if it was just one large partition. You'll probably not see any advantage using a dedicated /home.

---

### Post by al1x on 2011-09-07
So, If I resize the partition sda8 to 8GB I can preserve the files of sda8?I though that HD was random access and if I had to resize it &#921; could lose my files(?). :-?

---

### Post by al1x on 2011-09-07
So, if I resize the partition sda8 to 8GB I can preserve the files of sda8?I though that HD was random access and if I had to resize it &#921; could lose my files(?). :-?

---

### Post by btindie on 2011-09-07
It is, but when you use GParted it first resizes the NTFS filesystem down to the desired size, this includes moving the files to the correct location for the resizing operation. Finally it changes the partition size by updating the partition table.

---

### Post by al1x on 2011-09-07
oh ok, I didn't knew that..Thanks for the info!

---

