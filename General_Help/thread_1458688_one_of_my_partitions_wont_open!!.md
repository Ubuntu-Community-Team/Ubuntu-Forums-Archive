---
title: "one of my partitions wont open!!"
date: 2010-04-20
forum: General Help
---

### Post by facsimile on 2010-04-20
hey guys im new to ubuntu and i love it!!!!

i have a problem and i was wondering if somebody could help me.

i have 3 partitions one is for ubuntu another for windows7(so my wife can use it) and the other is for my files, like pics, music software etc.

in ubuntu i can see that drive open up pics and tunes, but when i run windows that drive does not show, or even the ubuntu partition.

does anybody know how to make it work?
thanks for advance!!!
ubuntu rules it was love at 1st sight:)

---

### Post by cdenley on 2010-04-20
The type of filesystem used on the third partition might be useful. In ubuntu, while the filesystem is mounted, run this command, then post the output.
```

mount

```

For ext3 or ext4 filesystems in Windows:
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)
Of course windows doesn't support linux filesystems out-of-the-box. The only way to access it is using an ext2 driver, since ext3 and ext4 should be backwards-compatible with ext2. I would suggest avoiding this, though. Windows isn't as good as linux when it comes to non-native filesystems.

---

### Post by facsimile on 2010-04-20
the type of partition is a nfts.
ill open up that link and give a try, thanks!!:P

---

### Post by cdenley on 2010-04-20
No reason for windows not to see ntfs filesystems. I haven't used the newer windows releases much at all, though.

---

### Post by facsimile on 2010-04-20
i also forgot to mention that when i run ubuntu in the 3rd drive is says win7 loader. does that have something to do with it not shwowing up?
:confused:

---

### Post by coffeecat on 2010-04-20
It might be helpful to see the details of your partition layout. I suspect you may have more than three. Open a terminal (Applications > Accessories) and post the output of:

```
sudo fdisk -l
```Please enclose the output in code tags by highlighting it in the message box and clicking on the # icon in the toolbar.

I don't follow this:

> **facsimile said:**
> i also forgot to mention that when i run ubuntu in the 3rd drive is says win7 loader. does that have something to do with it not shwowing up?
:confused:

Please clarify. Where does it say "Win7 loader"?

---

### Post by facsimile on 2010-04-20
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17848   143363036    7  HPFS/NTFS
/dev/sda2           24804       36483    93819600    7  HPFS/NTFS
/dev/sda3           17849       24803    55866037+   5  Extended
/dev/sda5           17849       24513    53536581   83  Linux
/dev/sda6           24514       24803     2329393+  82  Linux swap / Solaris


this what i get when i do the fdisk..
i changed the boot to sda1 thats where windows is at and sda2 is where my files are at, but when i open up windows i cant see the sda2 disk....

where it says win7 loader for sda2 is when you start the pc and have to select the operation system.

:P
so what can i do to see the sda2 in windows and open up the files??

thanks!!

---

### Post by coffeecat on 2010-04-21
> **facsimile said:**
> where it says win7 loader for sda2 is when you start the pc and have to select the operation system.

That's the grub menu, and that's odd. Grub *should* only configure a Windows loader entry if it finds Windows bootloader files in the partition. It shouldn't do so for any spare partition with no bootloading stuff in it. How did you create sda2, with Windows or with the Ubuntu partitioner? Did the partition originally contain a Windows operating system?

> **facsimile said:**
> so what can i do to see the sda2 in windows and open up the files??

At the moment, I don't know. As cdenley said, there's no reason why Windows shouldn't. But try this in Windows 7:

Control panel (change view to View by Large Icons) -> Administrative Tools -> Computer Management -> Disk Management. Can you see the second NTFS partition there? If you right-click on it, can you do anything with Right-Click > Change drive letter (or anything else that right-click might offer you)?

---

### Post by cdenley on 2010-04-21
Are you sure it is an NTFS filesystem? You still haven't posted the output from the "mount" command while it was mounted. Just because the partition table marks it as type "HPFS/NTFS" doesn't mean it actually contains an NTFS filesystem.

---

### Post by john newbuntu on 2010-04-21
Run the boot info script using a liveCD and please post the output of RESULTS.txt located on the desktop.  Credit goes to meierfra for this script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by facsimile on 2010-04-22
> **cdenley said:**
> Are you sure it is an NTFS filesystem? You still haven't posted the output from the "mount" command while it was mounted. Just because the partition table marks it as type "HPFS/NTFS" doesn't mean it actually contains an NTFS filesystem.



im sorry for being new and not knowing, but how can i run the mount command? 
:P

thanks!!!

---

### Post by coffeecat on 2010-04-22
> **facsimile said:**
> im sorry for being new and not knowing, but how can i run the mount command? 

From a terminal, as with the fdisk command. Simply:

```
mount
```

When someone says to run a command, the terminal is implied. :)

---

### Post by facsimile on 2010-04-24
hey guys i was no able to log in before, i did what coffecat say i went.

to Control panel (change view to View by Large Icons) -> Administrative Tools -> Computer Management -> Disk Management. Can you see the second NTFS partition there? If you right-click on it, can you do anything with Right-Click > Change drive letter (or anything else that right-click might offer you)?
__________________


and i see the disk where all my files are at,  but im not able to do anything with it, i did right click on it and ´put it as visible but still i cant see it in my computer or even open it up..
thanks!!

so what else can i do?:P

---

### Post by coffeecat on 2010-04-25
> **facsimile said:**
> 

so what else can i do?

Run the mount command (as asked for twice) in case that isn't an NTFS partition despite what the partition table is reporting.

---

### Post by facsimile on 2010-04-26
thanks!!!
sorry for that.

ok so i did type mount in the terminal and this is what i got.

facsimile@facsimile-desktop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/facsimile/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=facsimile)

---

### Post by cdenley on 2010-04-26
You're trying to figure out why windows doesn't detect /dev/sda2, right? Did you mount that filesystem in ubuntu before running the "mount" command so we can identify the filesystem type, as instructed? I only see /dev/sda5.

> **cdenley said:**
> In ubuntu, **while the filesystem is mounted**, run this command, then post the output.
```

mount

```


> **cdenley said:**
> You still haven't posted the output from the "mount" command **while it was mounted**.

---

