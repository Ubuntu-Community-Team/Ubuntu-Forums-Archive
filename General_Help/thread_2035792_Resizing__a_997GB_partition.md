---
title: "Resizing  a 997GB partition"
date: 2012-07-31
forum: General Help
---

### Post by Royalist on 2012-07-31
I have a dedicated already installed Ubuntu 1TB HDD  which, when setting up, I seem to have made the partitions not the way that I would have liked them to be.
Apart from the MBR the main partition /dev/sda1 is a 997GB partition ext4. There is an extension which houses a 3.5Gb swap partition.

This HDD is a clone apparently successfully made yesterday with 'dd'. Both disks are healthy. The clone has just been backed up also.

I would like to resize the clone sda1 downwards and make two new partitions in place. One mounted @ root greater than 30Gb and the other mounted @ /home with the residual capacity. All ext4.

I have read the GParted manual and feel quite confident of succeeding without loss of data, but I would be most grateful of any expert tips and warnings of pitfalls that I may not have thought of PLEASE?

This would be done with the disk unmounted by using a live USB stick.:)

---

### Post by oldfred on 2012-07-31
Are you going to keep both drives connected eventually. If so and it is a clone it has duplicate UUIDs and it will be best to change them now. But you have to update fstab, reinstall grub2 and make a few other changes. 

If drive is not ever going to be connected to same computer the duplicate UUIDs will not create any issue.

You should just be able to shrink / (root) and move/home. Only if you have a lot of data in / already may make it a multi-step process.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

It looks like you have already review similar info, if not:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

I find my own optimal partitioning plan is obsolete a year or two later. Usually I then buy another larger drive as I do not trust drives to last,  and then can reorganize. I left a lot of unallocated space on my 650GB drive a couple of years ago and all I have done is add 25GB / (root) partitions to try out the next version or test another install. But since I had the room I did not delete the older ones.

I also like to keep /home inside my / and move data only to data partitions, but that is primarily because I multi-boot and want to have the data available everywhere but not share /home.

---

### Post by Royalist on 2012-07-31
Thanks Oilfred. No, I just have a preference for monthly cloned backups. They will not both be connected for booting.

Only 6% of the 997Gb partition is in use and that is data and system.

Thanks for the tip about moving 'home'. I would probably have done it the hard way.

<I also like to keep /home inside my / and move data only to data  partitions, but that is primarily because I multi-boot and want to have  the data available everywhere but not share /home.>

Yes, I think I will do that. I also dual boot with Win XP on another separate disk.

Many thanks:D

---

### Post by oldfred on 2012-07-31
I have (more had since I am not using it) XP on my small drive and created a shared NTFS partition for any data I wanted in both XP and Ubuntu. I had profiles for Firefox & Thunderbird and all photos. Then Picasa could see same pictures, I had same bootkmarks & email without having to reboot.

I now put all new data in a Linux formated data partition, but still have the NTFS shared as I have not reorganized. 

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

---

### Post by Royalist on 2012-08-02
Thanks again Oldfred.

It is done and as yet no sign of any data loss and much tiddier. However, I am as yet unable to access logical data partitions, as I assume the owner is root. So I will have to try to remember the command to change that - CHROOM - I thought it was?

It seems that /home is best left in root, but the lower data sub directories I want to put into the "DATA" logical partition. I have been trying drag and drop, cause I'm lazy.

Regards

Roy:D

---

### Post by oldfred on 2012-08-02
If the partitions are on permanent drives, you should be automounting in fstab, that then sets permissions & ownership.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by Royalist on 2012-08-03
Fred, may I call you Fred?

I am in a quandary and I need you to tell me please, if I have committed a heinueous crime or not? 

By various means and mostly using GUI's where possible, I have gained the necessary permissions to both partitions and dragged & dropped files and directories into them. These means were unmounting, chown~ ing and chmod~ing and remounting. Never did I receive anything but negative result reports in terminal and the ls -l permission reports appear to be unchanged. By the use of Properties (right click in file system GUI) I can see that the ownership and permissions are satisfactory.

So, what please are the risks of NOT following your advice with Fstab etc? Is everything going to suddenly crash?

Also, I am concerned about whether I have actually copied the files and directories over, or have I just established symbolic links. Result of that will be to lose the lot when the originals are deleted. This must be easy to find out.

I do apologise for causing you so much trouble. Incidentally, nothing appears to change following an overnight shutdown and re-boot.

Thanks very much
Roy:(

---

### Post by oldfred on 2012-08-03
If you do not auto mount with fstab, you will have to manually mount with terminal or Nautilus. With nautilus you get a default mount, but any changes you made to permissions or ownership will stay if a Linux partition. With NTFS only the mounting controls permissions & ownership.

LInks will say they are links when you look at them in Nautilus. See my Documents & Downloads that have the -> to actual location. 

```
fred@fred-Precise:~$ ls -l
total 2004
drwxr-xr-x 2 root root    4096 Jun 14 13:08 bin
-rw------- 1 fred fred 1290151 Jul 20 14:38 bookmarks.html
-rwxrwxr-x 1 fred fred  113072 Dec 21  2011 bootinfoscript
-rw-rw-r-- 1 fred fred    3590 Apr 20 15:50 bug.crash
drwxrwxr-x 4 fred fred    4096 Jul 19 23:24 Calibre Library
drwxr-xr-x 2 fred fred    4096 Apr 18 15:48 Desktop
lrwxrwxrwx 1 root root      19 Mar 24 15:23 Documents -> /mnt/data/Documents
lrwxrwxrwx 1 root root      19 Mar 24 15:23 Downloads -> /mnt/data/Downloads

```

---

### Post by Royalist on 2012-08-03
Thanks Fred.

So my understanding is, that all is well as things are because the partitions in question are definitely all Linux. I do not think that my level of competence is up to tackling 'fstab' yet. I would probably do more harm than good.

Thanks for the advice re - links. One last question,  what does the 'b' preceding 'rwx' etc  signify please? This has been causing some confusion.

Now I will take myself off and stop bothering you.

Very many thanks.

Roy:D

---

### Post by oldfred on 2012-08-03
I knew blank was a file & d was directory, and from my post above knew l was link. But I had to look up details as I never paid attention before.

First letter is device type.

```
fred@fred-Precise:~$ ls -l /dev/sdb1
brw-rw---- 1 root disk 8, 17 Aug  1 13:51 /dev/sdb1

```

b is for block device or in my case above a partition.

[http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/](http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/)

---

### Post by Royalist on 2012-08-17
Thanks Oldfred,

I am coming on by leaps and bounds. I am going for fstab now, because automounting has stopped. blkid no problems there.

Fingers crossed :)

---

### Post by Royalist on 2012-08-20
Thanks again. I have now got to grips with Fstab and it works like a dream, except that the final three items below, have been rejected and so omitted from Fstab. 

roy@roy-desktop:/media/Data$ sudo blkid
[sudo] password for roy: 
/dev/sda1: LABEL="WD Windows" UUID="FBDE4CC4D6840840" TYPE="ntfs" 
/dev/sda5: LABEL="WD SATA Secondary Partition" UUID="CF609E7D9A560910" TYPE="ntfs" 
/dev/sdb1: LABEL="Ubuntu_11_10_Sys" UUID="6fbac1d1-f5ef-4b9a-bddc-dd73c3ffe0ff" TYPE="ext4" 
/dev/sdb5: UUID="79418029-2022-424f-8efd-daab256f0948" TYPE="swap" 
/dev/sdb6: LABEL="Reserve" UUID="a22b07cc-c2bc-4cdd-b779-889d20c44827" TYPE="ext4" 
/dev/sdb7: LABEL="Data" UUID="a162c63e-5973-42e6-a449-3cbb66b82a66" TYPE="ext4" 
/dev/sdc1: LABEL="Maxtor B/Up" UUID="98D82B9AD82B7622" TYPE="ntfs" 
/dev/sdd1: LABEL="Backup Windows XP" UUID="8828F9E728F9D462" TYPE="ntfs" 
/dev/sdd2: LABEL="Backup Linux" UUID="7E288DFA288DB227" TYPE="ntfs" 

I have tried 'dmask=027,fmask=137' and then 'dmask=000,fmask=111' without any luck. Am I using too many together perhaps? They are all USB devices. The mount point filenames, where spaces exist. were enclosed in quotation marks.
I hope you can help yet again please. Many thanks

---

### Post by oldfred on 2012-08-20
I am not sure about mounting USB devices with fstab. I have never tried that, and it might only work if they are always plugged in. I think any change would cause issues as fstab is more for permanent mounts.

See post #19  From Morbuis1 for more info:
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

---

### Post by Royalist on 2012-08-21
Thanks Oldfred. The external usb drives appear to be completely accessible in terminal, so there is no problem with fstab not including them. So many thanks for all your help and in particular 'mount -a' after editing fstab.

I haven't yet decided to move home and would like to find the discussion links that I thought you had previously included to me?  I have searched Ubuntu for that subject, but not found what I want. I do prefer the idea of maintaining the settings on re-installation and upgrade of the O.S. :)

---

### Post by oldfred on 2012-08-21
I think all these are the same but use different commands to copy the data. I prefer rsync,

# MoveHome.txt
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
If encrypted:
[http://askubuntu.com/questions/17332/how-can-i-move-an-encrypted-home-directory-to-another-partition](http://askubuntu.com/questions/17332/how-can-i-move-an-encrypted-home-directory-to-another-partition)

---

### Post by Royalist on 2012-08-22
Thanks It is done, quite easy, except all the permissions have not come over (as promised in "https://help.ubuntu.com/community/Partitioning/Home/Moving") and now this: -

roy@roy-desktop:~/Documents$ sudo chown roy:roy LINUX-TERMINAL-COMMANDS
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
roy@roy-desktop:~/Documents$ 

Where do we go from here please?

---

### Post by Royalist on 2012-08-22
More info for you, which may help

' /etc/sudoers is owned by uid 1000, should be 0'

I had previously followed the advice in 'http://www.psychocats.net/ubuntu/fixsudo' from recovery mode case 3: , but it has not "delivered the goods".

I am going to try again.

---

### Post by CharlesA on 2012-08-22
You would have to either boot into recovery mode or boot a live cd and mount the OS drive, then run this:

```
chown root:root /etc/sudoers
```

Make sure the permissions are set right too, they should be:

```

-r--r----- 1 root root 723 Jan 31  2012 /etc/sudoers

```

---

### Post by Royalist on 2012-08-22
I will be trying the latest recommendation straight away, but in the meantime I did
succeed with chown 0440  and chmod 0 and now we have: -

' /etc/sudoers is owned by gid 1000, should be 0'

Just to keep the ball rolling

---

### Post by CharlesA on 2012-08-22
Yeah, the owner needs to be changed, and that would fix that error.

---

### Post by Royalist on 2012-08-22
Thanks Charles, that did it. Sudo now is working again. However, I wasn't able to achieve exactly the Chmod settings you prescribed.

Now I am back to the original problem of ownership in numerous sub directories: -

'chown roy:roy /dir/dir/*  etc etc does not penetrate all the way down the tree. Is there another fast way of making all the previously accessible files available. I believe that making all the parent directories executable should do that, but how many levels will that go to?

Thanks

---

### Post by CharlesA on 2012-08-22
What folder did you chown roy:roy on ?

---

### Post by Royalist on 2012-08-22
Well for example at present I am trying to make the following accessible: -

'/Documents$ sudo chown roy:roy /home/roy/Documents/"Work Files 2011"/*'

"Work Files 2011"/* has numerous sub directories and I am finding that I have to go right to the last directory to change the ownership. '/"Work Files 2011"/*' does not permeate to the lower subs!

---

### Post by Royalist on 2012-08-22
```
sudo chown roy:roy /home/roy/Documents/"Work Files 2011"/*
roy@roy-desktop:~/Documents$ ls -l /home/roy/Documents/"Work Files 2011"/*
-rw-r--r-- 1 roy roy 157476 2012-08-22 11:50 /home/roy/Documents/Work Files 2011/LivingExpenses11_A.ods
-rw-r--r-- 1 roy roy 166536 2012-08-22 11:50 /home/roy/Documents/Work Files 2011/LivingExpenses11.ods
-rw-r--r-- 1 roy roy 146578 2012-08-22 11:50 /home/roy/Documents/Work Files 2011/phonelis.ods

/home/roy/Documents/Work Files 2011/Broadband:
total 4
drwxr-xr-x 2 root root 4096 2012-08-22 11:50 BT Account

/home/roy/Documents/Work Files 2011/Computer Hardware:
total 70888
-rw-r--r-- 1 root root 72431442 2012-08-22 11:50 Pentile_Test_6761.psd
-rw-r--r-- 1 root root   146798 2012-08-22 11:50 phonelis.ods
drwxr-xr-x 2 root root     4096 2012-08-22 11:50 Photo_Presentations
drwxr-xr-x 4 root root     4096 2012-08-22 11:50 Scilly_Isles_Tresco

/home/roy/Documents/Work Files 2011/Database:
total 20
-rw-r--r-- 1 root root 19692 2012-08-22 11:50 New_Phonelis.ods

/home/roy/Documents/Work Files 2011/Holidays:
total 24
-rw-r--r-- 1 root root 22065 2012-08-22 11:50 TRESCO HOLIDAY FINANCES March 2011_12

/home/roy/Documents/Work Files 2011/Household:
total 4392
-rw-r--r-- 1 root root 4493480 2012-08-22 11:50 Electrolux_Vacuum_Manual_Z4730.pdf

/home/roy/Documents/Work Files 2011/Linux Commands:
total 60
drwxr-xr-x 2 root root  4096 2012-08-22 11:50 Command Line
-rw-r--r-- 1 root root 42417 2012-08-22 11:50 Command_Line_Howto_install.html
drwxr-xr-x 2 root root  4096 2012-08-22 11:50 ConvertFilesystemToExt4_files
drwxr-xr-x 2 root root  4096 2012-08-22 11:50 LinuxFilesystemsExplained_files
drwxr-xr-x 3 root root  4096 2012-08-22 11:50 Linux Terminal Commands

/home/roy/Documents/Work Files 2011/Recipes:
total 240
-rw-r--r-- 1 root root  11135 2012-08-22 11:50 Crumble Topping.odt
drwxr-xr-x 5 root root   4096 2012-08-22 11:50 fish-pie--in-four-steps_files
-rw-r--r-- 1 root root 195592 2012-08-22 11:50 fish-pie--in-four-steps.html
drwxr-xr-x 2 root root   4096 2012-08-22 11:50 White_Bread_Sticks_files
-rw-r--r-- 1 root root   5956 2012-08-22 11:50 White_Bread_Sticks.html
-rw-r--r-- 1 root root  12952 2012-08-22 11:50 White_Bread_Sticks.odt
-rw-r--r-- 1 root root   3092 2012-08-22 11:50 White_Bread_Sticks.txt

/home/roy/Documents/Work Files 2011/Utilities:
total 108
drwxr-xr-x 2 root root   4096 2012-08-22 11:50 EDF
-rw-r--r-- 1 root root 104099 2012-08-22 11:50 UtilitiesCost.ods
roy@roy-desktop:~/Documents$
```

---

### Post by CharlesA on 2012-08-22
Wow.

Run this:

```
chown roy:roy -R ~
```

---

### Post by oldfred on 2012-08-22
the -R is recursion. It will work on all the lower levels as well. But you have to be very careful not to accidentally run it on any system partitions.

When you did the copy to the new partition did you leave off the parameters? Those should have preserved all the permissions & ownership.

sudo rsync [COLOR=Red]-aXS[/COLOR] --exclude='/*/.gvfs' /home/. /media/home/.

See man rsync for definitions of all the parameters. It is a long list.

---

### Post by CharlesA on 2012-08-22
> **oldfred said:**
> the -R is recursion. It will work on all the lower levels as well. But you have to be very careful not to accidentally run it on any system partitions.

Good warning. I've seen too many installs hosed by a typo. :mad:

---

### Post by Royalist on 2012-08-22
Very many thanks to you both. 'chown roy:roy -R ~' did the trick and I was very careful to only apply it to data archives. My understanding of the above is that '-R' is recursive and that '~' refers to home. This is safe I assume as there will be no system files in '/home/roy' now? I should have thought of using the '-R' rather fiddling about with '/*' , but would not have thought about the '~'

There is no question about having left out the 'rsync' parameters, I was meticulously careful with the all the syntax especially '-aXS'. There were some returns after the file comparisons, which I took to be resulting from the fact that the target directory for home was already occupied with data directories. I therefore expected that there would be some clearing up to do. However, I was delighted to find these directories sitting snugly where I wanted them to be.

So all seems to be well now. Thank you both very much for your patience. I will now mark the thread as closed.

---

### Post by CharlesA on 2012-08-22
Glad you got it working.

You can mark the thread as solved from thread tools. :)

---

