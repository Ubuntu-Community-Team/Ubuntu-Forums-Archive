---
title: "How to Access HDD with Ubuntu..."
date: 2010-04-20
forum: General Help
---

### Post by silkworm2.5 on 2010-04-20
Hi all.
Today I installed Ubuntu 9.10 to my HDD. I'm Lovin' it so far, (So much better than my Pendrive version), but I cant access the HDD.
My setup is this: Windows XP installed first, then I installed Ubuntu with a 10 GB desktop thing along side windows. I can now boot into either windows or Linux, But while in linux, I cant access My HDD.
Can anyone help or give me some advice Please?
TIA!

_______________________________
Linux FTW!

---

### Post by P4man on 2010-04-21
Is windows hibernated? If so, ubuntu will refuse to mount it.
If thats not the cause, please provide the output of

```
sudo fdisk -l
```

and

```
mount
```

---

### Post by silkworm2.5 on 2010-04-21
Thanks for the reply.
I tried it but it came up with these lines of code:
 
```
fdisk: invalid option -- '1'
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
[EMAIL="silkworm205@ubuntu:~$"]silkworm205@ubuntu:~$[/EMAIL] mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/silkworm205/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=silkworm205)

``` :confused:
 
I have no idea what it means, and no, windows wasn't in hibernation. I havent started it scince installing Ubuntu though, would that make any difference?
 
One more thing: I dont know if it's relevant or  not, but while at the GNU grub page for multiple booting, I have got Linux, and a recovery mode in there _twice each_.
 
And something else I just found. I looked at the path the boot loader showed for windows and it said it was /dev/sda1 so I went into the terminal and typed this in : **/dev/sda1 -mount** and the reply was **bash: /dev/sda: Permission Denied.**

---

### Post by P4man on 2010-04-21
You mistyped the first command. its FDISK -L in lowercase, letter l, not number 1. Use copy paste :)

If you want to try mounting from the command line, try this:

```
sudo mkdir /media/windows
```

that makes a folder in which we will try mounting your drive with:

```
sudo mount /dev/sda1 /media/windows -t ntfs
```

If that gives an error, post it here. If it doesnt, then you should be able to access your windows drive via /media/windows and then we can make this permanent later.

---

### Post by silkworm2.5 on 2010-04-21
Ah, Thanks for the correction. I'll change the font later so I don't mix letters up again :)

I typed in the first code and it made the folder, then when I activated the second code I got this:
```
silkworm205@ubuntu:~$ sudo mount /dev/sda1 /media/windows -t ntfs
fuse: mount failed: Device or resource busy
```

Would it have any affect on things that linux and windows share the same drive and **partition**? It would explain the part that mentions that it is busy...

Since running the code, it recognises the HDD, but I cant open it. I get an error box appear saying:
```
[B]Unable to mount location
[/B]Internal error: No mount object for mounted volume
```

___________
Always go for Linux

---

### Post by P4man on 2010-04-21
Is this a wubi install? (installed from within windows) ? If so, im not sure its possible, and if it is I have no idea how to do it.

---

### Post by silkworm2.5 on 2010-04-21
Yes it was installed within windows. I have data on here that I need and cannot risk losing it with partitioning tools. Or would it lose data from partitioning? 

If I cant access the HDD, then I'll just re-install Ubuntu with a bigger size and move all my stuff into it. I will be able to connect to another computer through a network link to hold the files while copying wont I? and even if it's windows?

EDIT: Is there any way to enlarge the install from within linux? (as it was a wubi install) or is there a way to back up my settings and data to restore into the new larger install?

---

### Post by Morbius1 on 2010-04-21
I don't know anything about wubi but I believe you'll find your files at /host and /media.

---

### Post by silkworm2.5 on 2010-04-21
Yes! That's it! It's in host Thank you both for your help!
\\:D/    \\:D/    \\:D/    \\:D/    \\:D/    \\:D/    \\:D/

---

### Post by Morbius1 on 2010-04-21
All I provided was comic relief, P4man deserves the credit for his deductive powers :)

---

### Post by P4man on 2010-04-21
> **silkworm2.5 said:**
> 

EDIT: Is there any way to enlarge the install from within linux? (as it was a wubi install) or is there a way to back up my settings and data to restore into the new larger install?

There used to be [LVPM ]("http://lubi.sourceforge.net/lvpm.html")to do that (move wubi to a dedicated partition), but it seems no longer supported and only seems to go to ubuntu 8.04. I wouldnt risk that. So  Im afraid the answer to both questions is, that there is no easy way, and its among the reasons I wholeheartedly discourage using wubi.

---

