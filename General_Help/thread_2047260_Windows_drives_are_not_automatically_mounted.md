---
title: "Windows drives are not automatically mounted"
date: 2012-08-24
forum: General Help
---

### Post by paichkash on 2012-08-24
hi
earlier i was using ubuntu 9.10 and whenever it booted up i would see the windows drives at desktop .. now i have 10.10 and its not the case.. However when i click on th Places in the top panel bar.. i can see my windows partiotions there and can click on it and then it is shown on desktop .. but only untill reboot.. i want it to show on the desktop by default ..
Thanks

---

### Post by SeijiSensei on 2012-08-24
First, find the UUID of your Windows partition using the command "**sudo blkid**".  You'll see a bunch of entries, one for each partition.  The Windows partition will have the ntfs type like this:

```
/dev/sda2: UUID="62D8A719D8A6EB0D" TYPE="ntfs"
```

Now copy the UUID, omitting the quotation marks, and use an editor like nano with sudo to add the corresponding line to /etc/fstab (i.e., "**sudo nano /etc/fstab**"):

```
UUID=62D8A719D8A6EB0D /windows  ntfs   defaults,umask=007,gid=46 0 0
```

Group 46 is the "plugdev" group on my machine.  Check the contents of /etc/group to make sure that's the right GID or use the correct one reported in that file.

I created the /windows mount point when I installed Ubuntu.  You may need to create one with "**sudo mkdir /windows**".  I always use the custom disk partitioning step during installation which gives you the opportunity to create a mount point for any Windows partitions and mount them automatically at boot.  I don't know how the other partitioning options handle existing Windows partitions.  If you choose this option during installation, it writes the correct /etc/fstab entries for you.

Now when you reboot, you should see the entire Windows filesystem mounted at /windows.  If you don't have the need to write files into the Windows partition, but just read from it, you might add ",ro" to the list of options in /etc/fstab.  Then you cannot accidentally damage the Windows installation.

---

### Post by Bucky Ball on 2012-08-24
Easier:

Open Software Centre or Synaptic Package Manager, look for and install:

ntfs-3g
ntfs-config

... then go to System>Administration>NTFS Configuration Tool. Select the partitions you want mounted at boot, ntfs-3g will rewrite the /etc/fstab file for you, reboot.

We are presuming these partitions are NTFS obviously. They could be FAT*.

@SeijiSensei: Mount points should really go in /mnt or /media, as in /mnt/Window or /media/NTFS_Drive. So 'sudo mkdir /mnt/Windows' unless you are in the /mnt directory already. ;)

---

### Post by paichkash on 2012-08-24
i m trying to follow this article
[http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm#Auto-Mount-Drives-at-System-Startup)

my winddows disk ois sda and it has three partitions ..  the storage device manager is showing three of them as sda1 , sda5,sda 6 .. and when i select sda1 it shows its type as swap .. why ? 

also when i select sda5 r sda6 it says 
/dev/sda5 hasn't been configured.
Do you want to configure it now?

---

### Post by Bucky Ball on 2012-08-24
Please reread my post. It will make it a cinch and done in five minutes. You may be wanting to learn more about coding in Linux, of course, in which case learning to rewrite the fstab is a good thing. Before going there and editing anything, although it is probably too late, back it up:
```

sudo cp /etc/fstab /etc/fstab.BAK
```Copy back if you screw things with:

```
sudo cp /etc/fstab.BAK /etc/fstab 
```Good luck. :wink:

Here's my NTFS line from fstab. I had nothing to do with it!

```
#Entry for /dev/sda10 :
UUID=6B8E2F2A62CEE191   /media/Misc     ntfs-3g defaults,locale=en_AU.UTF-8     0       0
```

---

### Post by paichkash on 2012-08-24
r@rDT:~$ sudo blkid
```
[sudo] password for r: 
/dev/sda1: LABEL="WIN" UUID="28F88F12F88EDD86" TYPE="ntfs" 
/dev/sda5: LABEL="SOFT" UUID="335D-080D" TYPE="vfat" 
/dev/sda6: LABEL="WIN" UUID="F84890F14890AFBC" TYPE="ntfs" 
/dev/sdb1: UUID="fa3717a0-dd1d-497e-a273-6a27b1e6a293" TYPE="ext4" 
/dev/sdb5: UUID="955e5e31-b47f-4ba3-83ea-f018c912ba1e" TYPE="swap"
```

also i have installed the ntfs-3g and ntfs-config but it only shows ntfs partitions not the fat32 one..

---

### Post by paichkash on 2012-08-24
@Bucky

here is my fstab after following ur advice but fat partition is not there also i have yet to reboot..
r@rDT:~$ cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb1 :
UUID=fa3717a0-dd1d-497e-a273-6a27b1e6a293    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=28F88F12F88EDD86    /media/WIN    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda6 :
UUID=F84890F14890AFBC    /media/WIN_    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb5 :
UUID=955e5e31-b47f-4ba3-83ea-f018c912ba1e    none    swap    sw    0    0

```[]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8LEzTdQ9E4AQaUK5gt.?p=mount%20fat%20partition%20fstab%20ubuntu&fr=altavista&fr2=sfp")

---

### Post by Bucky Ball on 2012-08-24
Well, looks like they're written in. As I half-guessed, you have FAT  also. That is slightly different. You will need to set that one up  manually. The first part using the UUID is the same (from memory) but  you can get the rest of the syntax from the first couple of links here:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8LEzTdQ9E4AQaUK5gt.?p=mount%20fat%20partition%20fstab%20ubuntu&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8LEzTdQ9E4AQaUK5gt.?p=mount%20fat%20partition%20fstab%20ubuntu&fr=altavista&fr2=sfp")

---

### Post by Morbius1 on 2012-08-24
This is the problem with using ntfs-config it always generates other questions ( amoung other problems ). Those lines look swell except they are read only. If you actually want to write to them:

Go into fstab directly as root:
```
gksu gedit /etc/fstab
```Change on both ntfs partitions:
> umask=0222to this:
> umask=0000While you're in there add another line at the end to mount your fat32 partition:
```
UUID=335D-080D /media/SOFT vfat defaults,utf8,umask=0000 0 2
```Then create the fat32 mount point:
[COLOR=Blue] EDIT: If you have the fat32 currently mounted you will need to unmount it first:[/COLOR]
```
 sudo umount /media/SOFT
```
[COLOR=Blue]Then create the permanent mount point:[/COLOR]
```
sudo mkdir /media/SOFT
```Unmount all these ntfs partitions:
```
sudo umount /media/WIN
sudo umount /media/WIN_

```And then run the following command that will test for errors in fstab and if there are none mount the partitions:
```
sudo mount -a
```

---

### Post by paichkash on 2012-08-24
^^ did as pointed out .. except the umask as i want them to be only avaiilable as readonly ..
..now its working after following ur advice ..
mywindows partitions are shown at desktop .. thanks all for their extremly quck response..

---

### Post by Morbius1 on 2012-08-24
Since this is solved I would be remiss if I did not point out that [COLOR=Blue]**SeijiSensei's**[/COLOR] post:
> UUID=62D8A719D8A6EB0D /windows  ntfs   defaults,umask=007,gid=46 0 0Is exactly the way the Ubuntu installer itself would have written it had you asked it to do so during the initial install of the OS. In fact if I remember correctly it even offers the /windows mount point as a predefined option.

---

### Post by SeijiSensei on 2012-08-25
> **Morbius1 said:**
> Since this is solved I would be remiss if I did not point out that [COLOR=Blue]**SeijiSensei's**[/COLOR] post:
Is exactly the way the Ubuntu installer itself would have written it had you asked it to do so during the initial install of the OS. In fact if I remember correctly it even offers the /windows mount point as a predefined option.

That entry in /etc/fstab was, in fact, created by the Ubuntu installer.  And, yes, the installer offers a choice of /dos and /windows as the mount point.  Frankly I don't think it much matters whether something is mounted to /mnt or /media or even just /something as long as you know where it is.  I generally put NFS shares and removable and secondary devices under /media.  I used /windows for the ntfs partition because Ubuntu offered it, and I didn't see any reason to put it anywhere else.  I would say I look at this partition about once every few months, so I don't really care much about where it is located within the filesystem tree.

---

### Post by paichkash on 2012-08-26
ok boys i marked this thread again as unsolved as my previous ubuntu went broke so idid again a fresh install.. now one of my windows partition is not shown again..

i  installed 
ntfs-3g
ntfs-config 
but when i click on ntfs configuration tool nothing happens tried running from terminal using 

gksu ntfs-config
got the following
```
r@rDR:~$ gksu ntfs-config
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

```

and 
sudo blkid
```
r@rDR:~$ sudo blkid
/dev/sdb1: UUID="073fc2be-1750-4481-a14c-5939b9034c80" TYPE="ext4" 
/dev/sdb5: UUID="8a30d1c4-298e-4aee-b280-d474063a9ccf" TYPE="swap" 
/dev/sda1: LABEL="WIN" UUID="28F88F12F88EDD86" TYPE="ntfs" 
/dev/sda5: LABEL="SOFT" UUID="335D-080D" TYPE="vfat" 
/dev/sda6: LABEL="WIN" UUID="F84890F14890AFBC" TYPE="ntfs" 
```

and
fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8a30d1c4-298e-4aee-b280-d474063a9ccf none            swap    sw              0       0

```

help again tried following previous responses but things were not same this time

---

### Post by Morbius1 on 2012-08-27
_**Please stop using ntfs-config.**_
ntfs-config is trying to use hal which Ubuntu hasn&#8217;t used in years. 

[1] If you currently have the ntfs and fat32 partitions mounted unmount them.

[2] Create the following folders:
```
sudo mkdir /media/Win1
sudo mkdir /media/Win6
sudo mkdir /media/SOFT

```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```Add the following lines to the end of fstab:
```
UUID=28F88F12F88EDD86 /media/Win1 ntfs defaults,nls=utf8,umask=0222 0 0
UUID=F84890F14890AFBC /media/Win6 ntfs defaults,nls=utf8,umask=0222 0 0
UUID=335D-080D /media/SOFT vfat defaults,utf8,umask=0000 0 2
```[4] Then run the following command to test for errors and mount the partitions:
```
sudo mount -a
```

---

### Post by Morbius1 on 2012-08-27
I completely missed this:

From fstab:
>  /dev/sda1       /               ext4    errors=remount-ro 0       1From blkid:
>  /dev/sda1: LABEL="WIN" UUID="28F88F12F88EDD86" TYPE="ntfs"That's not right.

That line need to be changed to:
```
 UUID=073fc2be-1750-4481-a14c-5939b9034c80 / ext4 errors=remount-ro 0       1
```You will need to run the InstallCD and in Live mode edit the fstab file to make that change.

[COLOR=Blue]**EDIT**[/COLOR]: Or since this is a fresh install just reinstall again. But this time don't even think about installing ntfs-config.

---

### Post by paichkash on 2012-08-30
> **Morbius1 said:**
> _**Please stop using ntfs-config.**_
ntfs-config is trying to use hal which Ubuntu hasn’t used in years. 

[1] If you currently have the ntfs and fat32 partitions mounted unmount them.

[2] Create the following folders:
```
sudo mkdir /media/Win1
sudo mkdir /media/Win6
sudo mkdir /media/SOFT

```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```Add the following lines to the end of fstab:
```
UUID=28F88F12F88EDD86 /media/Win1 ntfs defaults,nls=utf8,umask=0222 0 0
UUID=F84890F14890AFBC /media/Win6 ntfs defaults,nls=utf8,umask=0222 0 0
UUID=335D-080D /media/SOFT vfat defaults,utf8,umask=0000 0 2
```[4] Then run the following command to test for errors and mount the partitions:
```
sudo mount -a
```

> **Morbius1 said:**
> I completely missed this:

From fstab:
From blkid:
That's not right.

That line need to be changed to:
```
 UUID=073fc2be-1750-4481-a14c-5939b9034c80 / ext4 errors=remount-ro 0       1
```You will need to run the InstallCD and in Live mode edit the fstab file to make that change.

[COLOR=Blue]**EDIT**[/COLOR]: Or since this is a fresh install just reinstall again. But this time don't even think about installing ntfs-config.



now i am thoroughly confused.. 
y i need a reinstall now ? 

also i have two physical harddisks and during install i removed one harddisk inorder to use dvd rom.. after ubuntu is installed and ok.. i remove the dvd and attach the windows hdd.. and i have only one ext4 partition that is currently housing ubunutu. and its booting ok. how is the above line problemetic >

---

### Post by paichkash on 2012-08-30
also my fstab is now changed here is it
```

r@rDR:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/**sda1**	/	ext4	errors=remount-ro	0	1
/dev/**sda6**	/media/WIN	ntfs	defaults,nls=utf8,umask=0222	0	0
/dev/**sdb5**	none	swap	sw	0	0

```

its confusing me.. 
i have two physical harddisks .. one is windows hdd.. that has 3 partitions only.. one is fat32 two are ntfs.. and it contains no ext4 partitions.. but from above output its showing that i have ext4 partitoin on same harddisk as i have the ntfs one..? its not the case ...

my linux harddisk is having two partitions one is ext4 and one is swap..

---

### Post by Morbius1 on 2012-08-30
> **paichkash said:**
> also i have two physical harddisks and during install i removed one harddisk inorder to use dvd rom.. after ubuntu is installed and ok.. i remove the dvd and attach the windows hdd.. and i have only one ext4 partition that is currently housing ubunutu. 
Your fstab didn't come from thin air and it didn't come from the install process. It came about because you made it look that way by using Storage Device Manager. All of these fstab editors where written many years ago before Linux decided to go with UUID's instead of /dev/sdxy.

It's not your fault since they are in the repository. Mountmanager, ntfs-config, pysdm, and whatever else is in there should be purged from the repository so that things like this don't happen but I don't have a vote.

You installed Ubuntu without the other disk present and then after install reattached the disk. When your system boots it's anybody's guess which disk the system sees as sda and which one it sees as sdb. If you can actually boot into this system then just live with the inconsistency in fstab.

In the future allow the installer to do it's job and don't override things with any kind of fstab editor other than gedit. When you do that UUID's will be used and you will no longer have this sdxy mess becasue short of a reformat the UUID in unique and persistent..

---

