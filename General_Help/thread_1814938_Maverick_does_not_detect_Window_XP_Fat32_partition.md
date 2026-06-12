---
title: "Maverick does not detect Window XP Fat32 partition"
date: 2011-07-30
forum: General Help
---

### Post by CrankyOldMan on 2011-07-30
Hi!  

I have two machines, a laptop and a desktop which both boot 32 bit XP, or Ubuntu 10.10.    (The OS's run from separate partitions.)  When I have the laptop booted into Ubuntu, it recognizes the Windows partition and I can mount it for transferring files.   (Ubuntu also sees my data and swap partitions.) 

The desktop is a different matter.  It sees the Windows swap partition, but not my Windows partition.   Why not?    I have run GParted on the desktop, and it sees the WIndows partition.   But there is no Windows partition in the "Places" menu.

I use the Windows installation for CAD work, and the Ubuntu installation for secure internet and email work.  I need to be able to access the Windows partition from Ubuntu.  

Anyone have any ideas how to fix this?

---

### Post by oldfred on 2011-07-30
Are you talking network access from one computer to another or just the windows partition on the same drive?

If the same drive it should show. On mine it has a label and appears under that label (vendor serial number or something odd). Most computers show it just as the size like '122GB'.

I generally suggest not to mount the windows c: drive as read/write but as read only. Windows does not like a lot of activity from other systems writing into it. Ubuntu also shows all the normally hidden files & folders and it is too easy to accidentally move or erase something important. It is best to create a d: drive as a shared NTFS partition for read/write by both systems. Many windows users suggest a separate data partition so when you reinstall you do not have to reinstall all your data (backups still required).

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by CrankyOldMan on 2011-08-01
Thanks.  No network involved.  Ubuntu is not seeing all the partitions on the local drive.     I've had a lot of problems with Windows security (viruses, etc.), and so I am not planning on enabling the network for Windows.  I will download updates to the OS, applications, etc, from Ubuntu, and save them to the windows partition for later installation.  I'm not very concerned about deleting or overwriting a WIndows system file.

Got any idea how to fix this?

---

### Post by oldfred on 2011-08-01
The psychocats site linked above has a good explanation. See second half where she discusses vfat mounting.

Create a mount point and add an entry to fstab.

After any edit of fstab always run this to confirm that the edit is ok

sudo mount -a

---

### Post by CrankyOldMan on 2011-08-04
Thanks Oldfred.  I'll read up on this and give it a go.

---

### Post by CrankyOldMan on 2011-08-10
Oldfred,

Belated thanks for the advice.  I followed the instructions in the Pschocats link, made a mount point, and edited fstab.  The windows drive mounted just fine.  Only one small problem......  I can't right click on it, and unmount it.    The message I get is "only root can unmount /dev/sda5 from /media/windows.  Any way I can fix this?

Would I be out of line to bring up another issue in this thread?  One which might be related?    I noticed on my laptop, (which also runs Ubuntu 10.10), that there are a couple odd items in the "Places menu".  Links to drives or folders with very long names, which don't work.   They look like drive "block id's".   Can these links be deleted, or fixed?  I could not find them listed in fstab.

---

### Post by pjd99 on 2011-08-10
> **CrankyOldMan said:**
> 
Only one small problem......  I can't right click on it, and unmount it.    The message I get is "only root can unmount /dev/sda5 from /media/windows.  Any way I can fix this?


Because the entry is in fstab now, it is mounted by the system. You wont be able to unmount it as a regular user.

If you need to unmount it, run the following command:
```

sudo umount -l /media/windows

```

---

### Post by oldfred on 2011-08-11
Partitions you mount in /nedia or /home often show up twice in Nautilus' left panel. I mount in /mnt and link folders in to avoid the issue. But you can also do this:

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by CrankyOldMan on 2011-08-13
> **pjd99 said:**
> Because the entry is in fstab now, it is mounted by the system. You wont be able to unmount it as a regular user.

If you need to unmount it, run the following command:
```

sudo umount -l /media/windows

```


Thanks PJD99.   Not being able to unmount the drive with a right click of the mouse is not a big deal, but now I know how to do it from a terminal window.

---

### Post by CrankyOldMan on 2011-08-13
> **oldfred said:**
> Partitions you mount in /nedia or /home often show up twice in Nautilus' left panel. I mount in /mnt and link folders in to avoid the issue. But you can also do this:

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)


Oldfred,

Thanks also, but this time you lost me.  Probably because I hi-jacked the thread for a second issue.  (My bad.) 

Anyway, were you responding to my question about mounting and unmounting the windows partition on my desktop?  Or are you talking about the wierd entries I have in the "places" pulldown menu of my laptop?  If the latter, I'm afraid I gave you some bad information.  (That's what happens when I write a post depending on my memory.)  Anywa, the wierd entries in the places entry look like this.

version="1.0"?>
name= "current" mtime="1312039573" type="string">
name= "current" mtime="1308609237" type="string">

clicking on either of these gives me an error message, "could not open location".

---

