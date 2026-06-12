---
title: "I'm authenticating myself crazy - help!!"
date: 2009-12-22
forum: General Help
---

### Post by john1066 on 2009-12-22
So I have installed 9.10 on my disc - there is one user - lets call him ME. When I log in I give a password - I'm ok with that. When I try to access my D disc for the first time  I am asked to authenticate - I would rather not have that. When I install something I am asked to authenticate _ I would rather not have that also. So first question - how do I get rid of all these authentications? - they are driving me nuts.

Second question - my disc E is never visible until I specifically mount it - how do I get this to mount automatically?

And then. Under Vista I used Karins Replicator to back up my important folders to an external disc  - wonderfull program - really quick 30 seconds and all done - if there are no changes in a folder it just skips the backing up ( real common sense there). Unfortunately no Linux version. So what's the Ubuntu equivalent? I see there are many back up packages - far too many actually - I do not want to study for a Ph. D, in back up packages before I can make a choice.  So what is simple & quick & reliable?

Thanx,
John

---

### Post by Morbius1 on 2009-12-22
> When I try to access my D disc for the first time  I am asked to authenticate - I would rather not have that.> Second question - my disc E is never visible until I specifically mount it - how do I get this to mount automatically?I think you need to automount both those partitions at boot so you won't need to authenticate.

If you give us some information we can help you with that:
Open **Terminal**
Type **sudo blkid**
Type **cat /etc/fstab**
Note: those "l" in blkid are lower case "L"

---

### Post by Primefalcon on 2009-12-22
you can automount files using fstab but as for installing software and such, you'd need to enable root, which I cannot tell you to do here.....

decent fstab tutorials are here
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

if you want to mount a windows type filesystem such as ntfs, then here
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by starcraft.man on 2009-12-22
For backup, see this [wiki]("https://help.ubuntu.com/community/BackupYourSystem") and grsync. Should do the same job, maybe better? It does incremental synchronizing of folders. Also see simple backup suite, it does archives rather than sync. Read the pages for an explanation.

To get E to automatically mount, it needs to be in fstab. I believe there is a friendly graphical app for this called pysdm. To install:

```
sudo apt-get install pysdm
```
Should let ya configure drives as ya like, just be careful.

As to first question, that's a feature. If you want to forego all security warnings and authentication, maybe you'd prefer XP with it's default admin account and viruses? The authentication is the explained [here]("https://help.ubuntu.com/community/RootSudo"). I strongly advise you not to disable authentication. Please read the article, if you insist on doing so there are ways to fix it.

---

### Post by dasy2k1 on 2009-12-22
ubuntu in conmen with almost every other linux distro by default runs as an unprivilaged user. this means that you need extra privileges to do system admin stuff.

this is one of the main reasons that ubuntu is many more times more secure than certian other operating systems, 

by default ubuntu will not let you mound internal hard-drives as a user, but this can be changed by
going to system>administration>users and groups, 
and clicking properties on your own username (you will need to unlock first by clicking the keys and typing your password) then make sure "mount user space filesystems (FUSE)" is checked, 

that should solve your disk mounting problem, 

i would strongly recomend leaving the rest of the autentication in place as it serves to protect you form anyone malicious totally destroying your syestm

---

### Post by synapsys on 2009-12-22
Yeah, I guess security can be a real pain in the ask. It is still better than the alternative....

---

### Post by mc4man on 2009-12-22
I'm not too sure adding user to fuse addresses the need to authenticate the mounting of internal filesystems.
 
Plus in karmic auth. only lasts 300 secs by default

For the admin. user such auth. is unnecessary and has been addressed in lucid but not in karmic.
While there are 2 ways to change, the best way is this - 

create a file (because the file doesn't exist yet I'd copy and paste this carefully rather than manually copy

```
gksudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.DeviceKit.Disks.pkla 
```

Copy and Paste this inside and save (should show up as 4 lines

```
[No password required for admins]
Identity=unix-group:admin
Action=org.freedesktop.devicekit.disks.filesystem-*;org.freedesktop.devicekit.disks.change-system-internal
ResultActive=yes
```

That's all

---

### Post by john1066 on 2009-12-22
Output as follows (its all double dutch to me!)

jjs@jjs-laptop:~$ sudo blkid
[sudo] password for jjs: 
/dev/sda1: UUID="764E82E64E829E8D" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="02AA8395AA83843F" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="eed005f7-0fc8-4a9d-8091-6abcff4c3981" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="7850A8BE50A8850A" LABEL="Disc E" TYPE="ntfs" 
/dev/sdb1: UUID="886A01C91A923D46" LABEL="Disc D" TYPE="ntfs" 
/dev/sdb5: UUID="b3e0a859-365f-49e7-9111-e4052b1b94cd" TYPE="ext4" 
/dev/sdb6: UUID="c71f88ca-5bb0-4d6c-8da8-d66779c4fb5e" TYPE="swap" 
jjs@jjs-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=b3e0a859-365f-49e7-9111-e4052b1b94cd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c71f88ca-5bb0-4d6c-8da8-d66779c4fb5e none            swap    sw              0       0
jjs@jjs-laptop:~$

---

### Post by Morbius1 on 2009-12-22
Well you could do something like this. It's all in the terminal I'm afraid:

Open **Terminal**
Type **mkdir /home/jjs/DiskD**
Type **mkdir /home/jjs/DiskE**
Type **sudo su**
Type **echo "/dev/sdb1 /home/jjs/DiskD ntfs defaults,umask=007,gid=46 0 0" >> /etc/fstab**
Type **echo "/dev/sda4 /home/jjs/DiskE ntfs defaults,umask=007,gid=46 0 0" >> /etc/fstab**

There's a way to to this without rebooting but since I don't know what you've got mounted it's best to do a reboot.

---

### Post by john1066 on 2009-12-22
Okay - status report.

Solution proposed by dasy2k1 didn't do it.
Solution proposed by mc4man got it for disc d but not for disc e.
Solution proposed by morbius1 cracked it for both d and e discs. Great.

One other question. I suspect that dev/sda3 is the result of a failed ubuntu installation - would you agree? And if so how can I convert it to nfts and add it onto disc e?

Thanks to everybody who helped.

John

---

### Post by Morbius1 on 2009-12-22
>  I suspect that dev/sda3 is the result of a failed ubuntu installation - would you agree?Without knowing what's in sda3 I can't say. 

> And if so how can I convert it to nfts and add it onto disc e?If you have Vista installed on that system, it's best to do it in Vista. In windows just delete the partition and resize "E".
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

If you don't have vista I suppose you could use gparted, but I personally have never done that on a windows filesystem. I try to use linux tools for linux and windows tools for windows. I don't know if gparted will preserve the data.

---

### Post by john1066 on 2009-12-23
Regarding my question on ditching the stuff on sda3 and reusing it here is some further info -





Sudo fdisk gives the following info
 

 Disk /dev/sda: 320.1 GB, 320072933376 bytes 
 255 heads, 63 sectors/track, 38913 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x7579b316 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1               1        1306    10485760   27  Unknown 
 /dev/sda2   *        1306       20110   151041016    7  HPFS/NTFS 
 /dev/sda3           20110       21944    14732422   83  Linux 
 /dev/sda4           21945       38913   136303492+  12  Compaq diagnostics 
  
 Disk /dev/sdb: 320.1 GB, 320072933376 bytes 
 255 heads, 63 sectors/track, 38913 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x49400df9 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1   *           1       34344   275868148+   7  HPFS/NTFS 
 /dev/sdb2           34345       38913    36700492+   5  Extended 
 /dev/sdb5           34345       38720    35150188+  83  Linux 
 /dev/sdb6           38721       38913     1550241   82  Linux swap / Solaris 
 

 

 

 gparted info is as follows for sda3 , sdb5 and sdb6


            file sys       mount point      size      unused
sda3     ext3            -                      14.05    13.66
sdb5     ext4            /                      33.52     29.99
sdb6     linuxswap                           1.48
  

And when I look at whats in sd3, there is one folder called lost and found which I am not allowed to open.
 

 So my conclusion is that it is definitely something to do with Ubuntu and my suspicion is that it is the leftovers from an aborted ubuntu installation. My running Ubuntu installation is on the sdb stuff. I am almost certain I can ditch the stuff on sda3. My only worry is that is needed for the proper ubuntu installation on sdb2/5/6. Would appreciate an experts take on this.
 

 John

---

