---
title: "Mount of filesystem fail"
date: 2010-01-28
forum: General Help
---

### Post by musdem on 2010-01-28
When I try to boot into Ubuntu I get this error message:
Mount of filesystems failed.3d82d6-5dcb-494b-b2f0-fe9f157e9430
Any ideas on how to fix it? I have a duel boot with XP and Ubuntu 9.10.

---

### Post by jamesisin on 2010-01-28
Can you post the contents of your fstab file?

---

### Post by musdem on 2010-01-28
> **jamesisin said:**
> Can you post the contents of your fstab file?
How do I do that?

---

### Post by Morbius1 on 2010-01-28
Open **Terminal**
Type [B]cat /etc/fstab
[/B]
While you there you might want to post the output of another command:

Type **sudo blkid -c /dev/null**

Once you have the output in the Terminal, select "Edit" > "Select All" > Right click to "copy" then paste to the forum.

---

### Post by jamesisin on 2010-01-28
> **Morbius1 said:**
> While you there you might want to post the output of another command:

Type **sudo blkid -c /dev/null**

The command you want is simply:

blkid

and yes you should post that as well.

You can post these into code sections:

[NOPARSE]```
copy this and paste code here
```[/NOPARSE]

---

### Post by Morbius1 on 2010-01-28
> **jamesisin said:**
> The command you want is simply:

blkid

That is incorrect . The cache that blkid uses can become corrupted and display outdated information if there has been a lot of partition work such as label changes or even reformatting. It's best to use sudo blkid -c /dev/null to build the cache anew.

---

### Post by musdem on 2010-01-28
Ok but how do I access the terminal do I use a boot disc, remember I can get into Ubuntu.

---

### Post by Morbius1 on 2010-01-28
DOH , sorry about that, completely lost the whole point of the problem.

Boot to the LiveCD
Then open a terminal and type the blkid thing.

Then mount the partition that holds your linux install and navigate to /etc/fstab. If you simply double click it it will open in gedit. Just do a Select all and post to the forum from the LiveCD.

---

### Post by jamesisin on 2010-01-28
> **Morbius1 said:**
> That is incorrect . The cache that blkid uses can become corrupted and display outdated information if there has been a lot of partition work such as label changes or even reformatting. It's best to use sudo blkid -c /dev/null to build the cache anew.

Preparations.  Good idea.

```
sudo blkid -c /dev/null
blkid
```

---

### Post by musdem on 2010-01-28
Never mind I just booted it and now for some reason Ubuntu works again, thanks anyway.

---

### Post by musdem on 2010-01-31
ok it stoped working again same thing i did what you said and here are the results:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D20CCDC90CCDA935" TYPE="ntfs" 
/dev/sda5: UUID="3cd6a602-f08d-4d38-82b9-b0fb7b3a31b4" TYPE="swap" 
/dev/sdb1: UUID="6e3d82d6-5dcb-494b-b2f0-fe9f157e9430" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e32484ca-1983-4fc2-8f26-a15a69bf8ccb" TYPE="swap" 
/dev/sdc1: UUID="40284A46284A3AE4" LABEL="My Book" TYPE="ntfs" 
ubuntu@ubuntu:~$

---

### Post by jamesisin on 2010-02-01
The original error message you posted is for the drive with the UUID 3d82d6-5dcb-494b-b2f0-fe9f157e9430.  This drive is not listed in your blkid output.

Please also post the contents of your fstab file (located at /etc/fstab ).  You can view the contents with this command:

gedit /etc/fstab

[NOPARSE]```
copy this line and paste contents here
```[/NOPARSE]

> **musdem said:**
> $ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D20CCDC90CCDA935" TYPE="ntfs" 
/dev/sda5: UUID="3cd6a602-f08d-4d38-82b9-b0fb7b3a31b4" TYPE="swap" 
/dev/sdb1: UUID="6e3d82d6-5dcb-494b-b2f0-fe9f157e9430" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e32484ca-1983-4fc2-8f26-a15a69bf8ccb" TYPE="swap" 
/dev/sdc1: UUID="40284A46284A3AE4" LABEL="My Book" TYPE="ntfs"

I see three drives (sda, sdb, and sdc); how many physical drives do you have connected to this machine?

It also appears that you have two installations of Ubuntu (unless you are running from your CD and sda or sdb is your CD drive).  Can you confirm this?

---

### Post by musdem on 2010-02-01
Ok here are the contents of the file:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sdb5 swap swap defaults 0 0

Also I have 2 internal 1 TB hard drives and 1 external 2 TB hard drive for windows backups, and I am doing this from a CD.

---

### Post by jamesisin on 2010-02-01
What I would like to see is the fstab of your system (not the CD).  Can you mount your OS partition and navigate to that /etc/fstab while running the CD?

---

### Post by blueshiftoverwatch on 2010-02-01
Maybe [this]("http://ubuntuforums.org/showthread.php?t=1383551") will help.

---

### Post by musdem on 2010-02-02
sorry that was dumb of me here is the one from my installation:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e32484ca-1983-4fc2-8f26-a15a69bf8ccb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Morbius1 on 2010-02-02
Did anyone else notice something peculiar about all this ( other than at one point a simple reboot fixed it ).

The system complains of this:
> Mount of filesystems failed.[COLOR=Blue]3d82d6[/COLOR]-[COLOR=Blue]5dcb-494b-b2f0-fe9f157e9430[/COLOR]That UUID is not in the blkid nor is it in fstab, but this one is:
> 6e[COLOR=Blue]3d82d6[/COLOR]-[COLOR=Blue]5dcb-494b-b2f0-fe9f157e9430[/COLOR]Now it's entirely possible given the length of the number that you could have that amount of similarity between two different UUID's but it does look strange to me. Is the system truncating the UUID?

For what it's worth , because I really have no other idea as to what is wrong, I would do this if it were my system:

I would change this in fstab:
```
UUID=6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 / ext3 relatime,errors=remount-ro 0 1
```To this:
```
/dev/sdb1 / ext3 relatime,errors=remount-ro 0 1
```

---

### Post by musdem on 2010-02-02
actually it was checking the file system 6e3d82d6-5dcb-494b-b2f0-fe9f157e9430 at start up it got to i think 52% then it gave me the message though when this began it didn't.

---

### Post by musdem on 2010-02-04
OK I tried your method and it still didn't work, is it possible that the file is corrupt?

---

