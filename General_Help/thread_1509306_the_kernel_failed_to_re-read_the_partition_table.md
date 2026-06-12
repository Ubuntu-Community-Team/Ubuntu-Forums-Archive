---
title: "the kernel failed to re-read the partition table"
date: 2010-06-14
forum: General Help
---

### Post by ubeautu on 2010-06-14
Today I decided to completely removed my windows partition and the secret windows restore partition. (just not using windows any more - despite having expensive software on that partition) Well, in my naivety i used Disk Utility typing 'sudo palimpsest' to unmount the drive and tried to turn it in to a ext4 partition so I could store stuff on it. Unfortuantly it just kind of unmounted it. 

After some forum searching I gave up on Disc Utility and tried using GParted. Here is 
my current predicament:



[IMG]http://farm5.static.flickr.com/4039/4698686087_1a030419ca_b.jpg[/IMG]
The unallocated is just dev\sda1 after I tried to delete it, but I still cannot format the unallocated partition as it thinks it is busy: here is my drive info and the error from my terminal:
------------

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3bef74b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   172666619    86333278+  83  Linux
/dev/sda3       172677119   312576704    69949793    f  W95 Ext'd (LBA)
/dev/sda5       172677120   308581416    67952148+  83  Linux
/dev/sda6       308592648   312576704     1992028+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a6138bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    b  W95 FAT32
((me:~$ gksudo gparted
error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourselfdaniel@daniel-asus:~$ Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.
Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.
Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.
Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.
Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.
Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.

---------------

thanks for any easy solution you can offer me - Sorry I have a bit to learn about partitioning drives -

---

### Post by john newbuntu on 2010-06-14
For a good measure, reboot your system.  Log back with a liveCD and then format the partition using gparted or otherwise.

Wait a minute. Was /dev/sda1 a linux partition used by the system.  If so, what was it used for? That appears to have been deleted too along with /dev/sda2, which could be a problem depending on what was on it.

---

### Post by ubeautu on 2010-06-14
I think sda1 is what has become of my deleting of  sda1 and sda2. I think sda1 was the hidden windows restore and sda2 was the main windows install. 

Also when I restart grub is trying to mount /windows but cannot. I assue that will be the last thing I will have to fix when I get the problem partion(s) fixed.

---

### Post by john newbuntu on 2010-06-14
Then I take it that you have formatted it to ext3 or ext4.  I am also assuming that you are using grub2 and not grub-legacy.  If so read on:

You will need to install grub to the MBR using an ubuntu liveCD/USB.  Follow step#13 from this link by drs305 (Note that in your case, sdXY=sda5 and sdX=sda):
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
You do not have to mount the /boot partition.  Then reboot and check.

---

### Post by ubeautu on 2010-06-14
thanks John. Good assuming.  will give it a go in the next hour.

---

### Post by ubeautu on 2010-06-14
also John, does it matter that sda5 and sda6 appear to nested in sda3 in gparted?

---

### Post by john newbuntu on 2010-06-14
No Ubeautu. sda5 and sda6 are what are called as 'logical partitions' within an 'extended partition' or a container, if I may call it called /dev/sda3.

You could later on extend /dev/sda5 with the unalllocated 5+GB space unless you have it for a different purpose.

---

### Post by ubeautu on 2010-06-14
One last question before I try it: the instructions you said that I should not mount the /boot partion (which i guess is sda5?) on the linked instructions it asks to type :

sudo grub-install --root-directory=/mnt /dev/sdX
If I am not mounting sda5 should I put in '/mnt' after 'directory="?

Thank you

---

### Post by ubeautu on 2010-06-14
ok back from the live disk with no joy. 

I ran gparted and it was just the same effect as what happend when i try to format the unallocated partition - would not do it. 

So i did not managed to formate the space and next I tried to install grub -

I tired to do it by mounting but it said I was unable to mount sda5 - does not exist. Is that because it is a virtual partition? should I be trying to mount sda3? The error report said tor the grub install was: "cannot create directory 'mnt/boot': no such file or directory' - 

Any ideas? Perhaps there is some other program i should be using to format the problem unallocated partition?

---

### Post by The Cog on 2010-06-14
You should have no trouble formatting the unallocated space from a live CD. But first, you have to create a partition in there (sda1 perhaps?). Unallocated means there is not even a partition there to format. In gparted, I think that just creating a partition there will also format it to the filesystem you ask for. Then you have to mess with fstab to get it to mount at boot.

Which brings us to the subject of not being able to mount /windows any more. No surprises there. But that's not GRUB, that's coming from Linux as it reads /etc/fstab to find out what partitions need mounting. You should delete the entry for the windows partition now, or it will bitch about it every time you boot.

You should not have to do anything to grub. No need to reconfigure or reinstall it. You will be booting from sda5 just as before.

---

### Post by john newbuntu on 2010-06-14
Are you able to boot into ubuntu successfully?

If not, boot from your liveCD, and run:
sudo fdisk -l
you should have seen /dev/sda5 listed as a linux partition.  Next, if you continue with these commands:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```it should have re-install grub in the MBR.  But if you are saying that it complained about /boot, it is possible that /boot is corrupt or was installed in some other partition.

Also, stay in the liveCD and post the output of the file /mnt/etc/fstab.

Also post the output of "sudo blkid -c /dev/null"

---

### Post by ubeautu on 2010-06-14
From the live cd, I could not format sda1 in sudo gparted so I tried with Disk Utility (what I stuffed it up with) and it seemed to have formated it. Now it's called storage. But gparted still doesn't like that drive - won't reformat it. Also I did manage to re-install grub from the ubuntu but not from the live CD. Some of the big errors I keep getting in gparted include:
"Kernel failed to read partition, device or resource busy"  " Critical murrine_style_draw_box height>=-1 failed"

My output of "sudo blkid -c /dev/null":
/dev/sda1: LABEL="Storage" UUID="0a28b3ef-523e-42e6-9706-3245a4cf84c6" TYPE="ext4" 
/dev/sda5: LABEL="Ubuntu" UUID="6cc434db-dedb-4a52-a0d3-a7c467617230" TYPE="ext4" 
/dev/sda6: UUID="3b5a38bc-c013-46fd-961b-844ea0fd5065" TYPE="swap"

But then after trying to format it an extra time in gparted dev/sda1 is broken again and does not appear in 'blkid'

---

### Post by ezsit on 2010-06-14
> From the live cd, I could not format sda1 in sudo gparted so I tried with Disk Utility (what I stuffed it up with) and it seemed to have formated it. Now it's called storage. But gparted still doesn't like that drive - won't reformat it.

In all this time did you ever turn SWAP OFF before attempting to reformat? As long as SWAP is ON, gparted will not want to format any partitions since the drive is IN USE at the time.

You should be able to do this from within a running Ubuntu system since you are not messing with any system partitions. Open a terminal and:

**sudo swapoff -a**

Then open the Disk Utility or gparted and do what you need to do, reformat the partition. See if that works.

---

### Post by ubeautu on 2010-06-14
ok tried to turn swap off but I am not sure if it is off. Still got same error when I went in to gparted and tried to format sda 1. here is the report of the crash from gparted:

[COLOR=#000000][FONT=Times New Roman]GParted 0.5.1
Libparted 2.2
**Format /dev/sda1 as ext4**  00:00:05    ( ERROR )    calibrate /dev/sda1  00:00:00    ( SUCCESS )    [I]path: /dev/sda1
start: 63
end: 172666619
size: 172666557 (82.33 GiB)[/I]set partition type on /dev/sda1  00:00:05    ( ERROR )libparted messages    ( INFO )    *Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.**WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy). As a result, it may not reflect all of your changes until after reboot.**Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.**WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy). As a result, it may not reflect all of your changes until after reboot.*========================================
[/FONT][/COLOR]

---

### Post by ubeautu on 2010-06-14
Thanks guys for your help. I am almost there. I could not stop the swap in the command line, but when I right clicked on the swap file in gparted and turned off the swap and was able to format sda1. After that, I was able to re-install grub in sda5. Now I have a formatted partition sda1 that I can view in Ubuntu but I cannot copy files to it. It can be mounted and opened but it has a small file called 'lost+found' I am guessing that formatting sda1 was not enough, do i need to add something to the first sector or MBR sort of thing?

---

### Post by john newbuntu on 2010-06-14
First reboot.  Where is the mountpoint of /dev/sda1?  If you do "cat /etc/mtab", it lists the mount points.  It is the second column after /dev/sda1.  See if it is mounted "ro" instead of "rw".  If so, remount it as read-write.  Post any errors that you might get:
sudo mount -o remount,rw  yourmountpoint

OR

first unmount /dev/sda1 and run
```
mount -t ext4 /dev/sda1 /media/wherever
```Create the /media/wherever directory first.  Actually it could be any directory anywhere.

---

### Post by ubeautu on 2010-06-15
My current blkid output for "sudo blkid -c /dev/null" is:
> /dev/sda1: UUID="7765d36f-1165-4a67-a3d4-6fea3e890ccc" TYPE="ext4"My "cat /etc/mtab" is:
> /dev/sda1 /media/7765d36f-1165-4a67-a3d4-6fea3e890ccc ext4 rw,nosuid,nodev,uhelper=udisks 0 0Do you mean that I should do a general unmount of sda1 and a more specific mounting of /dev/sda1 /media/...? Is that problem that it is not properly mounted?

ps. I am also a bit concerned that the disc is formatted at 88gb but has 4.3GB of hidden files. Is that normal or is it part of the problem?

[IMG]http://farm5.static.flickr.com/4041/4703043760_b58ece82bb_b.jpg[/IMG]

This is what it looks like when I open it in ubuntu

[IMG]http://farm5.static.flickr.com/4005/4702407811_e54c87196d_b.jpg[/IMG]

---

### Post by john newbuntu on 2010-06-15
That looks ok to me.  I would suggest unmounting /dev/sda1 and running a file system check on it.  You can run it from your terminal since you do not have anything system files on it.
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```If this gives any errors, then run:
```
sudo e2fsck -f -y -v /dev/sda1
```If there are any errors that this clears, then just mount it using command line and see if you are able to use it.

Also that label on sda1 looks ugly long.  Change it to something meaningful - if you wish to do so.

Edit: Add or edit the following line in your /etc/fstab using "gksu gedit /etc/fstab" (Note: you can use UUID instead of /dev/sda1):
```
/dev/sda1  /media/storage    ext4    defaults        0       2
```
Also create and change the ownership of /media/storage directory to your userid as follows: "sudo chown userid:userid /media/storage"

---

### Post by ezsit on 2010-06-15
> I am also a bit concerned that the disc is formatted at 88gb but has 4.3GB of hidden files. Is that normal or is it part of the problem?

This looks fine. Filesystem metadata takes space to store, the filesystem journal takes space, and 5% of the drive is always reserved for root use, so 4.3 GiB from the total seems about right.

> Is that problem that it is not properly mounted?
The problem is the drive is being mounted without user permission to write to the drive. In /etc/fstab file you could try:

/dev/sda1  /media/storage  ext4 auto,users,exec 0 2


This should give you access to the filesystem.

---

### Post by ubeautu on 2010-06-16
Thanks very much John, Ezsit and Cog. With all your help I now have the partition mounting with permission and I am able to copy files there. I had a quick search about how to fix my grub boot up menu so it doesn't display options for non existent partitions (windows vista and windows recovery). If any of you know a quick solution for this, I would appreciate it, otherwise I will trawl the net some more. Oh, and can i edit the name of 'lost+found' to '.lost+found' to make it a hidden file without breaking things?

Thanks again.

---

### Post by john newbuntu on 2010-06-16
Glad we could help.  It should be as simple as running "sudo update-grub" from a terminal.

Edit: At some point you have turned swap off.  Please turn it on if you have not done so using "sudo swapon -a".

---

