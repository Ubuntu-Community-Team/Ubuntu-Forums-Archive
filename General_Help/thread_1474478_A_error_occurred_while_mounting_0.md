---
title: "A error occurred while mounting 0"
date: 2010-05-06
forum: General Help
---

### Post by bangde on 2010-05-06
I have upgraded my system from 9.10 to  10.04. I get the following error when i start  my computer.


A error occurred while Mounting O

Press s to skip or M to manual mount

How can I fix this error

This is my fstab below, what do i need to do to correct this startup problem.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
  /proc                                       /proc          proc         defaults                      0  0  
# / was on /dev/sda6 during installation
UUID=5663d1d1-6bee-438c-aea6-5d9f31204d96  /              ext4         errors=remount-ro             0  1  
  sw              0       0
 /dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  
 /dev/sda6                                  /media/sda6    ext3         errors=remount-ro,users,user  0  0

---

### Post by nitstorm on 2010-05-06
Can you please post the output of 
```

sudo blkid

```

---

### Post by bangde on 2010-05-07
this is the output

/dev/sda5: LABEL="Sheldon Extra" UUID="5663d1d1-6bee-438c-aea6-5d9f31204d96" TYPE="ext4" 
/dev/sda6: LABEL="Sheldon (HD)" UUID="b9bf4428-0e15-4152-95c0-72fe089a800d" TYPE="ext3" 
bangde@Monkey:~$

---

### Post by WorMzy on 2010-05-07
Delete the "sw 0 0" line from your fstab (gksudo gedit /etc/fstab).

You have no swap partition, but for some reason you have the remnants of a swap partition mounting line.

---

### Post by dowtish on 2010-05-11
[http://ubuntuforums.org/showthread.php?p=9280291#post9280291](http://ubuntuforums.org/showthread.php?p=9280291#post9280291)

---

### Post by bangde on 2010-05-22
> **WorMzy said:**
> Delete the "sw 0 0" line from your fstab (sudo gedit /etc/fstab).

You have no swap partition, but for some reason you have the remnants of a swap partition mounting line.


That worked for me. 

Thank you so much for the help.

:P

---

### Post by roritor on 2010-06-08
Hey guys,

I have the same problem. When I boot Ubuntu 10.04 I get an error halfway through boot, while still on the boot screen that says UBUNTU in the middle of the screen with the five little red dots underneath it. 
It will suddenly say:

An error occurred while mounting 0

Press S to skip mounting or M for manual recovery

I checked the above solution which worked for the original guy who started this thread however I, unlike this fellow, DO have a swap partition which I do not want to remove from my fstab file. 
My fstab file reads as follows:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=20966bc7-9393-49fc-8223-9f3ac54395ac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d04b8ea6-888d-46ae-806a-a97d94aa97e3 none            swap    sw              0       0
# This is the mount point for the Big-Brain Neuronics drive
//Big-Brain/Volume_1 /media/Neuronics cifs
username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode      0       0
# This is the mount point for the Big-Brain Mneumonics drive
//Big-Brain/Volume_2 /media/Mneumonics cifs
username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode      0       0

I originally had each of the network shares just say:

guest,uid=1000,iocharset=utf8,codepage=unicode,unicode

as it was written at [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) however it made no noticeable difference.


And when I run blkid it reads:

/dev/sda1: UUID="20966bc7-9393-49fc-8223-9f3ac54395ac" TYPE="ext4" 
/dev/sda5: UUID="d04b8ea6-888d-46ae-806a-a97d94aa97e3" TYPE="swap" 
/dev/sdb1: LABEL="POTATO CHIP" UUID="76B6C0C1B6C082DB" TYPE="ntfs" 

Potato Chip is my SD card, it must have put that line in by itself. What I am trying to do here is have two network shares attempt to mount automatically upon startup. I added those last to lines in to do just that. The mounting does work, if after booting completes I run a terminal and manually type:

sudo mount -a

It then asks for my root pass and when I type it in, it gives me this error:

mount: mount point 0 does not exist

and then proceeds to mount the first drive, asks for my pass again, gives the same error again and then proceeds to mount the second drive.

I have added Big-Brain to my /etc/hosts file with the static IP of 192.168.0.151, which I can ping just fine using the IP or the host name, which is obvious seeing as how the drives DO mount, after the errors.

I'm stumped. Any ideas?

BTW I'm pretty new to Linux...sorry for the rambling post but when I read forums, I tend to notice a certain amount of time is wasted by people asking for this or that information and I thought it might be easier if I tried to include all info plus my goals in the first post.

Thanks heaps!

---

### Post by WorMzy on 2010-06-08
I don't know if it's the way you've copied and pasted it, but the two network shares are on multiple lines. You should have one fstab entry per line. Adding a linebreak in the middle of an entry will cause fstab to treat it as two entries. Also, you have a space between the "c" and the "o" of codepage in both entries, which makes fstab think you've moved onto the next part of the entry. Replace the lines with these:

```
//Big-Brain/Volume_1 /media/Neuronics cifs username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//Big-Brain/Volume_2 /media/Mneumonics cifs username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
```

---

### Post by roritor on 2010-06-08
Thanks WorMzy! That worked great. About the extra space in codepage, that must have just been the way I cut and pasted it. I am not sure how that happened but when I checked the fstab file there was no extra space. What was wrong was that I had guest=,etc on a second line. I guess I did that because I was looking at the instructions on the website mentioned in my original post. If I had cut and pasted it, it would have come as a single line.

Anyway, I cut and pasted your lines and they work without a hitch. 

BTW what will happen when I'm away from the server and I boot, will I get some sort of error because it can't find the shares? Or will it just not mount them? Preferably the second scenario...  :-)

Anyway, thanks again...

---

### Post by WorMzy on 2010-06-09
I'm not sure, I've never worked with network shares or anything of that ilk. But at a guess, it'll probably report the same error as before ("Press S to skip mounting or M for manual recovery"). There's probably a way to make the errors silent, possibly by using "errors=ignore" or "errors=skip" or "errors=silent" as an mount option, but I can't find any information regarding it.


You're welcome btw. Happy to help. :)

---

### Post by boodain on 2010-11-09
I am having the same problem: A error occurred while Mounting O
When I run sudo blkid, this is what I get: 
/dev/sda1: UUID="d90768a9-0610-4968-943d-69ee257087fa" TYPE="ext4" 
/dev/sda2: LABEL="New Volume" UUID="43b27488-c7dd-4f76-ab90-749571537d50" TYPE="ext4" 

I have deleted the sw 0 0 line from fstab but it did not work.
I am a newbie and I was messing around with partitions to dual boot windows. Needless to say it did not work!

Could you please help??

---

### Post by WorMzy on 2010-11-09
We need the contents of /etc/fstab to examine.

When trying to edit that file, did you open it with root privileges? Your used doesn't have write permissions on it, so you need root privileges to make the necessary changes.

```
gksu gedit /etc/fstab
```

---

### Post by boodain on 2010-11-09
Yes I did. This is what is in fstab now:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
#Entry for /dev/sda5 :
defaults,nls=utf8,umask=0222	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

Must I still make changes here or do you think there is a different problem?

Thanks for your fast reply WorMzy.

---

### Post by WorMzy on 2010-11-10
You need to remove > defaults,nls=utf8,umask=0222 0 0
It's another malformed fstab line which is causing the problem.

---

### Post by boodain on 2010-11-10
That fixed the problem. Really appreciate the help. Thanks

---

### Post by lanetherif on 2010-11-21
Hi,

the same problem here... When I add a line for sda2, I get this message and when I don't sda2 is not auto-mounted...

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda5 during installation
UUID=2dbaac0d-8df8-4630-8a95-b6ba837ba956  /            ext4  defaults                 0  1  
/dev/sda4                                  /media/sda4  ext4  defaults                 0  0  
/dev/sda3                                  /media/sda3  ext4  
defaults                         0  0  
/dev/sda2                                  /media/sda2  ext4
defaults                         0  0
              
```and this is blkid:
```
/dev/sda2: LABEL="Muzikli" UUID="c913b620-b3dd-4ab3-8b83-3e20184610bf" TYPE="ext4" 
/dev/sda3: UUID="b7831a23-e4ed-4fd3-b81c-807eebb06d80" TYPE="ext4" 
/dev/sda4: LABEL="Filmli" UUID="dd990450-e201-4cfa-a195-f833d165f031" TYPE="ext4" 
/dev/sda5: UUID="2dbaac0d-8df8-4630-8a95-b6ba837ba956" TYPE="ext4" 

```What should I change?
Thanks...

---

### Post by WorMzy on 2010-11-21
Both sda2 and sda3 entries are on two lines. Remove the linebreaks in these entries. You could also change the last "0" on the sda2/3/4 entries to "2". Your fstab file should read like this (2's optional):

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point> <type> <options>           <dump><pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda5 during installation
UUID=2dbaac0d-8df8-4630-8a95-b6ba837ba956  /            ext4  defaults                 0  1  
/dev/sda4                                  /media/sda4  ext4  defaults                 0  2  
/dev/sda3                                  /media/sda3  ext4  defaults                 0  2  
/dev/sda2                                  /media/sda2  ext4  defaults                 0  2
```

---

### Post by lanetherif on 2010-11-21
> **WorMzy said:**
> Both sda2 and sda3 entries are on two lines. Remove the linebreaks in these entries. You could also change the last "0" on the sda2/3/4 entries to "2". Your fstab file should read like this (2's optional):

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                           <mount point> <type> <options>           <dump><pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda5 during installation
UUID=2dbaac0d-8df8-4630-8a95-b6ba837ba956  /            ext4  defaults                 0  1  
/dev/sda4                                  /media/sda4  ext4  defaults                 0  2  
/dev/sda3                                  /media/sda3  ext4  defaults                 0  2  
/dev/sda2                                  /media/sda2  ext4  defaults                 0  2
```


Thanks for the swift answer. :) Now it works.

---

### Post by roritor on 2010-11-22
Yeah, WorMzy is pretty awesome like that! 8-)

---

### Post by cylo on 2010-12-08
I'm very new here, this is my first post.  I too upgraded from  9.10 to 10.4.  Once the upgrade was complete and requesting a reboot, I get the message "An error occurred while mounting", but unlike the others in this thread, there's no further indication of what it's trying to mount.  

 Going into manual recovery mode and looking at other posts here, I tried the 'blkid' command, and compared it to my fstab.  My fstab does not mention a /dev/sda drive, but the blkid command does, and it's type 'NTFS'.  It appears to be my separate drive for the dual boot system (windoze is other drive).  It seems that the ubuntu side has partially forgotten the dual boot, even though GRUB controls the dual boot, and still successfully takes me into Windows if i select it. 

 Am I on the right track, and if so how to I tell teh ubuntu side to ignore and not to mount the sda drive?  I don't access the windows drive when booted into ubuntu, though i know I could.

Any tips?

---

### Post by WorMzy on 2010-12-08
blkid just tells you what's available on your computer, nothing more. In most cases it list something that isn't in your fstab, this is no cause for concern. If you want, post your fstab file and blkid output here, and we can take a look at it. Also, if you can run
```
sudo mount -a
``` in a terminal, it may give some indication as to what's happening. (If it just appears to do nothing, then that means it hasn't found a problem)

---

### Post by cylo on 2010-12-08
Thanks, I figured out the problem.  The fstab retained two lines, 
"/dev/sdb1"   and
"/dev/sdb5",

along with the new version UUID=xxxx lines.  Those old /dev lines did not get the treatment I've seen elsewhere in this post i.e. "/dev/sdb1 was previously blah, blah" preceded by comment #.  I assume the update process was supposed to do that.

Anyway, I deleted those two lines and it booted up fine.  Now to see what other remnants are laying around!

Even though I figured out my issue, I want to thank every one who takes the time to post.  I got many clues from previous postings, and like the other person said, I hope to get good enough with linux to be able to contribute to the forums.  Thanks for making it a little bit easier to get from underneath windows.

---

### Post by sakoto on 2010-12-28
Hello, I am experiencing a similar problem. I tried to set up quota for users and cannot mount.......

Result of blkid
/dev/sda2: UUID="5E2EAF392EAF08DB" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="78eeaf6c-e21c-4b9f-a1b2-148613469ef4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="7313d237-2125-4abd-829e-d2320ac83d81" TYPE="swap" 
/dev/sda7: UUID="a4554dae-700d-4cbc-88f8-b8b96b78508b" TYPE="ext4" 
/dev/sda8: UUID="bbd6a0ed-78c1-46ee-9d83-e651bfcd4f11" TYPE="ext4" 
/dev/sda9: UUID="141dfdbb-3f07-4ea3-82be-b5e1c9ad0477" TYPE="ext4"

/etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=141dfdbb-3f07-4ea3-82be-b5e1c9ad0477 /               ext4    errors=remount-ro,usrquota=aquota.usr,grpquota=aquota.grp,jqfmt=vfsv0 0       1
# swap was on /dev/sda6 during installation
UUID=7313d237-2125-4abd-829e-d2320ac83d81 none            swap    sw              0       0


Please, could you check a see where the problem lies?
Thanks,

sakoto

---

### Post by WorMzy on 2010-12-28
> **sakoto said:**
> Hello, I am experiencing a similar problem. I tried to set up quota for users and cannot mount.......

Result of blkid
/dev/sda2: UUID="5E2EAF392EAF08DB" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="78eeaf6c-e21c-4b9f-a1b2-148613469ef4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="7313d237-2125-4abd-829e-d2320ac83d81" TYPE="swap" 
                 7313d237-2125-4abd-829e-d2320ac83d81
/dev/sda7: UUID="a4554dae-700d-4cbc-88f8-b8b96b78508b" TYPE="ext4" 
/dev/sda8: UUID="bbd6a0ed-78c1-46ee-9d83-e651bfcd4f11" TYPE="ext4" 
/dev/sda9: UUID="141dfdbb-3f07-4ea3-82be-b5e1c9ad0477" TYPE="ext4"
                 141dfdbb-3f07-4ea3-82be-b5e1c9ad0477
/etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=141dfdbb-3f07-4ea3-82be-b5e1c9ad0477 /               ext4    errors=remount-ro,usrquota=aquota.usr,grpquota=aquota.grp,jqfmt=vfsv0 0       1
# swap was on /dev/sda6 during installation
UUID=7313d237-2125-4abd-829e-d2320ac83d81 none            swap    sw              0       0


Please, could you check a see where the problem lies?
Thanks,

sakoto

I'm no expert at setting up disk quotas, but from what I've read, you seem to be mixing journalled and unjournalled mount options. Also, I don't know if using quotas on the root (/) partition is a good idea, the info I've found seems to be focusing on /home partitions, but like I said, I'm no expert here, so I'll assume you know what you're doing.

If you want unjournalled, use the following in fstab:
```
UUID=141dfdbb-3f07-4ea3-82be-b5e1c9ad0477 /               ext4    errors=remount-ro**,usrquota,grpquota** 0       1
```

If you want journalled, use the following in fstab:
```
UUID=141dfdbb-3f07-4ea3-82be-b5e1c9ad0477 /               ext4    errors=remount-ro**,usrjquota=aquota.user,grpjquota=aquota.grp,jqfmt=vfsv0** 0       1
```

Just to make sure you can tell the difference, the unjounalled entry uses "usrquota", and the journalled entry uses "usr**j**quota" and an argument as well as the extra part "jqfmt=vfsv0". You were mixing the two, which may have caused the problem.

---

### Post by sakoto on 2010-12-30
Thanks WorMzy, you're great!

---

### Post by dooda on 2011-02-12
I also get that error message.  Not sure what's going on.  Any help would be appreciated :

ben@ben-System-Product-Name:~$ **sudo more /etc/fstab**
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc        proc  nodev,noexec,nosuid  0  0  
/dev/sda2  /            ext4  errors=remount-ro    0  1  
/dev/sda3  none         swap  sw                   0  0  
/dev/sdb1  /media/sdb1  ntfs  defaults             0  0  
/dev/sda4  /media/sda4  ntfs  defaults             0  0
//CINEMA/ntfs-sda3-cave    /media/ntfs-sda3-cave        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_
mode=0777 0 0

+++

ben@ben-System-Product-Name:~$ **sudo blkid**   
/dev/sda1: UUID="A2DC7608DC75D6CF" TYPE="ntfs" 
/dev/sda2: UUID="0190847f-fd0e-4214-9eb0-a9c929b15128" TYPE="ext4" 
/dev/sda3: UUID="28799df0-ad3b-4474-88c3-5d9c4fb409ab" TYPE="swap" 
/dev/sda4: LABEL="forbackups" UUID="1EB039BB471567D1" TYPE="ntfs" 
/dev/sdb1: LABEL="blank_lucien" UUID="172BCD61BB3F75F7" TYPE="ntfs" 

+++

ben@ben-System-Product-Name:~$ **sudo fdisk -l**

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff25cd07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35839968+   7  HPFS/NTFS
/dev/sda2            4462        5741    10268672   83  Linux
/dev/sda3            5741        5773      262144   82  Linux swap / Solaris
/dev/sda4            5773       60802   442015744    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c43e02e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

---

### Post by WorMzy on 2011-02-12
> **dooda said:**
> I also get that error message.  Not sure what's going on.  Any help would be appreciated :

ben@ben-System-Product-Name:~$ **sudo more /etc/fstab**
...
//CINEMA/ntfs-sda3-cave    /media/ntfs-sda3-cave        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_
mode=0777 0 0

The problem lies here. There is a line break after "dir_" which should not be there. Delete the line break so it looks like this:

```
//CINEMA/ntfs-sda3-cave    /media/ntfs-sda3-cave        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by dooda on 2011-02-12
> **WorMzy said:**
> The problem lies here. There is a line break after "dir_" which should not be there. Delete the line break so it looks like this:

```
//CINEMA/ntfs-sda3-cave    /media/ntfs-sda3-cave        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Thanks, that did the trick.

---

### Post by jake91 on 2011-03-30
I am having the same problem, but mine occurred after a power outage while the machine was still running.

blkid

jacob@Carbon:~$ blkid
/dev/sda1: UUID="ed557c15-b445-46d9-a878-b07a889c3589" TYPE="ext2" 
/dev/sda5: UUID="F0oPZr-ARmJ-47bw-0Aq0-6joo-CHKT-9AQZ2D" TYPE="LVM2_member" 
/dev/sdb1: UUID="8d277fb8-67c2-43bf-970b-5735d0b7d6db" TYPE="ext3" 
/dev/sdc1: UUID="2e8b6d04-361a-4a12-908c-5bc20fa47822" TYPE="ext2" 
/dev/mapper/Carbon-root: UUID="a682d64e-c36f-4713-8fcd-7fcdc339bc15" TYPE="ext4" 
/dev/mapper/Carbon-swap_1: UUID="e16b4021-6540-4647-8259-d535971a6dde" TYPE="swap"

sudo nano /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Carbon-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ed557c15-b445-46d9-a878-b07a889c3589 /boot           ext2    defaults        0       2
/dev/mapper/Carbon-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=8d277fb8-67c2-43bf-970b-5735d0b7d6db       /home/jacob/media       ext3    defaults        0       2
# /dev/sdc1
UUID=2e8b6d04-361a-4a12-908c-5bc20fa47822       /home/jacob/video       ext2    defaults        0       2
#nfs
/home/jacob     /export/jacob   none    bind    0       0


Thanks for any help in advance!:)

---

### Post by jake91 on 2011-03-30
Too expand on my previous post, I am also getting the following errors:

/dev/sdc1 was not cleanly unmounted, check forced.
/dev/mapper/Carbon-root: clean, 178619/2334720 files, 922399/9325568 blocks
/dev/sdb1: clean, 33944/61054976 files, 131471098/244190000 blocks
/dev/sda1: clean, 237/124496 files, 112072/248832 blocks
init: ureadahead-other main process (879) terminated with status 4
An error occurred while mounting /export/jacob
mount: mount point /export/jacob does not exist
mountall: mount /export/jacob [889] terminated with status 32
mountall: Filesystem could not be mounted: /export/jacob
Press S to skip mounting or M for manual recovery

---

### Post by killerkhatiby009 on 2011-04-25
I am having the same problem here is the result from my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda6	/	ext4	errors=remount-ro	0	1
0	0
/dev/sda5	/media/Data	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sda3	/media/OS_Install	ntfs-3g	defaults,locale=en_US.UTF-8	0	0

---

### Post by roritor on 2011-09-26
Hey WorMzy,

A couple years ago, in this very thread, you gave me some good advice and sorted out an issue I was having with trying to mount two network shares automatically upon startup from a file server on my network. I set up the auto-mounts on a little netbook. You had me put in:

# This is the mount point for the Big-Brain Neuronics drive
//Big-Brain/Volume_1 /media/Neuronics cifs username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
# This is the mount point for the Big-Brain Mneumonics drive
//Big-Brain/Volume_2 /media/Mneumonics cifs username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

which I already had in fstab, except I had the entries on two different lines, which confused fstab. You had me fix it so both entries were in one line each.

However, I have just set up a a dual-boot on my desktop PC with the same distro of Ubuntu. I literally copied those two lines from the fstab file from my netbook and placed them into the fstab file on my PC. I made sure that the mount folders were where they needed to be. However when I boot up, I get nothing.

So I dropped into a terminal and tried to manually "mount /media/Neuronics" and "mount /media/Mneumonics". For both tries I get:

mount: wrong fs type, bad option, bad superblock on //Big-Brain/Volume_1,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and 

mount: wrong fs type, bad option, bad superblock on //Big-Brain/Volume_2,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Just for the hell of it, I changed the fs type in the fstab file to "auto" (without the quotes), in which case I get:

mount: special device //Big-Brain/Volume_1 does not exist

And then also for the hell of it I changed the fs to "proc" (also without the quotes) and then when I type mount /media/Neuronics it just jumps down a line back to the command prompt, as if it did it successfully, however nothing actually shows up on my desktop.

Any ideas? As of now, I've just changed it back to "cifs" on both entries.

In addition, I am trying to get an external USB floppy drive to work on either my netbook or my desktop in Ubuntu. In my netbook, I plug in the floppy drive and the floppy powers up and spins a bit but absolutely nothing happens on the netbook. On the desktop, when I plug it in, the drive clicks on for a minute and when I click on "Computer" in my list of devices (all my hard disks and stuff) "Floppy Drive" shows up. If I double click it, absolutely nothing happens (as opposed to if I double click one of my hard disks, it goes into the drives root directory). The floppy doesn't click on or anything, either. If I unplug the drive, "Floppy Drive" disappears from the list. I know for a fact that the drive is good because it works fine under windows and shows up in BIOS and I use it to flash BIOS and/or boot into OS's. I've tried to set up a mount point with fstab (using /mnt and /media) but I can't use fd0, I reckon because the floppy drive isn't connected to the motherboards floppy drive ribbon cable point. 

I know I tend to ramble on a bit but I always reckon it's easier to give you all the information up front as opposed to having you need to ask me a bunch of questions. However, if there's anything I've missed or anything you need me to check, let me know.

Just want to say, any help you can throw my way is VERY much appreciated. Seriously.

Thanks in advance for your time and for any help you provide me!

---

### Post by WorMzy on 2011-09-26
> However, I have just set up a a dual-boot on my desktop PC with the same distro of Ubuntu.

By that, do you mean the exact same version (10.04) or do you mean a more recent version? If you have 10.04, make sure that you've installed the smbfs package.

Natty, Maverick and Oneiric, however, all have a separate package for the cifs utilities (cifs-utils), so make sure you've installed that instead of (or as well as) the smbfs package.

I'm not sure about the floppy drive. You might want to create a new thread about it. Try disconnecting the floppy drive, then reconnecting it and then running ```
dmesg | tail
``` paste the output into a new thread, and I'll take a look at it.


@jake91: Sorry for the late reply, if you're still waiting for an answer, it appears that your problem is that the folder "/export/jacob" doesn't exist; try recreating it.

```
sudo mkdir -p /export/jacob
```

@killerkhatiby009: Sorry for the late reply, if you're still waiting for an answer, you just need to delete the third line ("0 0") from your fstab

```
gksudo gedit /etc/fstab
```

---

### Post by roritor on 2011-09-26
WorMzy, 
How are you so awesome? :-)

Still no go on the floppy but yeah, I'll start a new thread. 

Got my network shares working now though...

Not to sidetrack the thread, but any good reason to upgrade 10.10 to Natty Narwhal?

---

### Post by WorMzy on 2011-09-26
I eat my vegetables. ;)

Well, 10.10 will only be supported up until April next year, but that's when the next LTS (Long Term Support -- supported for three years) version is expected to come out, soooo, you can upgrade now if you want (you'll have access to more up-to-date applications), or, if you're comfortable using 10.10, you can wait for it to "expire", then upgrade to the LTS release.

Also, 11.04 (Natty) and 11.10 (Oneiric) both use the Unity desktop environment by default, so you might want to check that out on a LiveCD before you make the plunge and upgrade. I believe that you can choose to use the classic GNOME2 environment in 11.04, but I'm not sure whether that'll be available in 10.10 (GNOME 3 was released in April, and the GNOME 2 environment was effectively killed off by the GNOME developers)

Anyway, that command I posted regarding your floppy wouldn't have any effect on the problem itself, it'd just provide some information about whether the system is recognising it correctly or not.

---

### Post by CarterD13 on 2012-04-01
Hey guys I am having an issue with boot and have the similar problem with "A error occurred while mounting 0" after I skip that I have another error which states "serious errors with mounting sdb1" 

Here is my fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda1 during installation
UUID=15885993-bac4-44f1-9472-dc4c09ffb39e  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sda5 during installation
UUID=4fd873c2-da6c-4179-94c2-907f6241409d  none         swap  

sw                       0  0  

/dev/sdb1                                  /media/sdb1  ntfs  nls=iso8859-1,umask=000  0  2  

This is the blkid
/dev/sda1: UUID="15885993-bac4-44f1-9472-dc4c09ffb39e" TYPE="ext4" 
/dev/sda5: UUID="4fd873c2-da6c-4179-94c2-907f6241409d" TYPE="swap" 
/dev/sdb1: LABEL="Expanded Disk" UUID="1094C4C294C4AB92" TYPE="ntfs"

I am brand new to Ubuntu and have only been using it for a few days. I appreciate the information in here and have attempted a few changes shown in earlier posts but still no luck.

---

### Post by CarterD13 on 2012-04-05
Oh well I reinstalled ubuntu and started over again unfortunately I had to do that.

---

### Post by WorMzy on 2012-04-06
Sorry for the late reply, I've been away on holiday for the past week and a bit. The problem was these lines:

```
UUID=4fd873c2-da6c-4179-94c2-907f6241409d none swap

sw 0 0 
```

I guess it's a little late now, but in case you were wondering, those lines should have just been one:

```
UUID=4fd873c2-da6c-4179-94c2-907f6241409d none swap sw 0 0
```

---

