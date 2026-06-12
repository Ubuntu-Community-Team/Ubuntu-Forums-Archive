---
title: "Cannot see windows directory from Ubuntu"
date: 2011-09-13
forum: General Help
---

### Post by insane9 on 2011-09-13
This is how my laptop looks. I can see my 96gb Ubuntu partition but i cannot see my Windows partition.

How do i permanently mount it? 

can someone post step-by-step instructions on how to do it?

Thanks



[IMG]http://img221.imageshack.us/img221/3653/screenshotdxe.png[/IMG]

---

### Post by Grenage on 2011-09-13
Interesting; Please post the output of these two commands:

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by insane9 on 2011-09-13
> **Grenage said:**
> Interesting; Please post the output of these two commands:

```
cat /etc/fstab
sudo fdisk -l
```

Here are the outputs:


si@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/sda1 /media/windows ntfs-fuse auto,gid=1001,umask=0002 0 0

si@ubuntu:~$ sudo fdisk -l
[sudo] password for si: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013173

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       17904   143703572+   7  HPFS/NTFS
/dev/sda3           17904       30402   100390913    f  W95 Ext'd (LBA)
/dev/sda5           30015       30402     3108864   82  Linux swap / Solaris
/dev/sda6           17904       29517    93280256   83  Linux
/dev/sda7           29517       30015     3998720   82  Linux swap / Solaris

Partition table entries are not in disk order




Grenage, i went on the 'Disk Utility' and i found i can access my windows files because they're mounted on /Host

How can i get that to show up in my 'computer' screen?

thanks again

---

### Post by Grenage on 2011-09-13
I'm not familiar with /Host; is this a WUBI installation?  Devices mounted under /media will show up in Nautilus (the file manager), and fstab sayso that it should be mounting there.

If this is a Wubi install then I should stop here; I've never used Wubi before, and I could easily end up breaking your system.

---

### Post by wadd92 on 2011-09-13
> **insane9 said:**
> Grenage, i went on the 'Disk Utility' and i found i can access my windows files because they're mounted on /Host

How can i get that to show up in my 'computer' screen?

thanks again

ALT + F2 type in /host and press enter

---

### Post by insane9 on 2011-09-13
> **Grenage said:**
> I'm not familiar with /Host; is this a WUBI installation?  Devices mounted under /media will show up in Nautilus (the file manager), and fstab sayso that it should be mounting there.

If this is a Wubi install then I should stop here; I've never used Wubi before, and I could easily end up breaking your system.

Yes it's a wubi install. (Windows + Ubuntu dual boot)

Here is how i see my Windows files:

[IMG]http://img69.imageshack.us/img69/652/directoryk.jpg[/IMG]



But as i say, i want the Windows partition to appear in 'computer' section as a mount

---

### Post by insane9 on 2011-09-13
> **wadd92 said:**
> ALT + F2 type in /host and press enter

I understand that, but i want /host to appear in 'Places'

---

### Post by Mark Phelps on 2011-09-13
If you're intending to WRITE info to your Windows filesystem from inside Ubuntu -- that's a bad idea.  Remember, you're running off a filesystem that is INSIDE the Windows filesystem.  So, if you accidentally corrupt the Windows filesystem (i.e., shutting down your laptop without first cleanly unmounting the filesystem), you run  the risk of corrupting the Windows filesystem -- and then, Ubuntu may not boot anymore.

---

### Post by coffeecat on 2011-09-13
> **Mark Phelps said:**
> If you're intending to WRITE info to your Windows filesystem from inside Ubuntu -- that's a bad idea.  Remember, you're running off a filesystem that is INSIDE the Windows filesystem.  So, if you accidentally corrupt the Windows filesystem (i.e., shutting down your laptop without first cleanly unmounting the filesystem), you run  the risk of corrupting the Windows filesystem -- and then, Ubuntu may not boot anymore.

+1
+101
+1001

> **insane9 said:**
> I understand that, but i want /host to appear in 'Places'

@insane9, I'm going to tell you how to get "host" into Places, but first I want you to read Mark Phelps post. Then read it again. And again. Do you get the message? :)

Now - open Nautilus and then open the host folder. Go to the bookmarks menu and "add bookmark". It will appear in the Places pane on the left. You can rename it if you want.

---

### Post by insane9 on 2011-09-13
> **coffeecat said:**
> +1
+101
+1001



@insane9, I'm going to tell you how to get "host" into Places, but first I want you to read Mark Phelps post. Then read it again. And again. Do you get the message? :)

Now - open Nautilus and then open the host folder. Go to the bookmarks menu and "add bookmark". It will appear in the Places pane on the left. You can rename it if you want.

thanks for that coffee but i've still got the same problem.. Here's a pic to show you where i want the shortcut to be:

[IMG]http://img801.imageshack.us/img801/6898/screenshot1lp.png[/IMG]

I want it to be under the 96 GF File System shortcut.


And don't worry, i wont mess up my Ubuntu. I just want to view files that are on my Windows partition, not edit anything dangerous. It seems silly to have to duplicate them to see them, thats all :)

So up to now, i can view my Windows directory via /Host  , but i want a shortcut in the 
'Places' at the top.

When i did what you suggested, it put a shortcut on the left, but not places on the menu at the top.

p.s

I am using Ubuntu, just a linux-mint theme

---

### Post by coffeecat on 2011-09-13
> **insane9 said:**
> p.s

I am using Ubuntu, just a linux-mint theme

I'll take your word for it! :wink:

> **insane9 said:**
> 
When i did what you suggested, it put a shortcut on the left, but not places on the menu at the top.

Hmm. To be honest I'm slightly puzzled. I can see you are using the classic gnome desktop, but which version of Ubuntu, 10.04 or 10.10?

All I can say is that I have a wubi installation of Ubuntu on my netbook, but version 11.04. I usually use the Unity desktop, but I've just logged into the classic desktop (which is very similar to the 10.04 and 10.10 versions). I've bookmarked my host folder. If I open a Nautilus window, "host" appears at the bottom of the list under the Downloads folder in the left Places pane of the window. So it seems you are seeing that. But if I open the Places menu from the top panel, you can see what I see from my attached screenshot, and clearly you are not seeing that in your system.

I don't have access to a wubi installation of 10.04 or 10.10, so I can't double-check this. Perhaps someone else can comment. At the very least - if I understand you correctly - you now have a shortcut to the host folder in a Nautilus window. All you have to do is to open Nautilus from any of those in the Places menu and then click on host in the left pane. Two clicks instead of one. :)

By the way, just to add to the business of being careful inside your hosts folder. I know you've got the message, but it's important to remember that since Windows and Linux permissions systems are different, Ubuntu will not respect Windows permissions. Therefore it is possible to accidentally delete an important Windows system file from Ubuntu that would not be deletable in Windows. Take care!

---

### Post by insane9 on 2011-09-13
> **coffeecat said:**
> I'll take your word for it! :wink:



Hmm. To be honest I'm slightly puzzled. I can see you are using the classic gnome desktop, but which version of Ubuntu, 10.04 or 10.10?


All I can say is that I have a wubi installation of Ubuntu on my netbook, but version 11.04. I usually use the Unity desktop, but I've just logged into the classic desktop (which is very similar to the 10.04 and 10.10 versions). I've bookmarked my host folder. If I open a Nautilus window, "host" appears at the bottom of the list under the Downloads folder in the left Places pane of the window. So it seems you are seeing that. But if I open the Places menu from the top panel, you can see what I see from my attached screenshot, and clearly you are not seeing that in your system.

I don't have access to a wubi installation of 10.04 or 10.10, so I can't double-check this. Perhaps someone else can comment. At the very least - if I understand you correctly - you now have a shortcut to the host folder in a Nautilus window. All you have to do is to open Nautilus from any of those in the Places menu and then click on host in the left pane. Two clicks instead of one. :)


I'm using a wubi install of ubuntu 11.04 in classic mode with a linux mint theme :)

I'll mess around some more, i'm sure it's something simple i'm not doing. thanks for the help :)

P.S

what you described in your screenshot is absolutely correct, that's what should happen but isn't happening for me

---

