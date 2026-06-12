---
title: "Trying to figure out how to access Windows partition"
date: 2010-10-18
forum: General Help
---

### Post by Leopardson on 2010-10-18
So, I've got a ridiculously complicated problem.

I have a desktop, a cellphone. I do NOT HAVE a disk drive, a USB stick or anything of the sort.

The desktop has two operating systems on a single hard drive: Ubuntu 10.04 and Windows 7.
I need to get internet access in Windows 7.

The cellphone is a Galaxy S Vibrant, and is tethered so that I can connect to the internet through it.
In Ubuntu, the tether is automatically supported. I just shove a USB cable between the cellphone and the phone and I've got internet in Linux.
But in Windows, the tether needs drivers. I can't connect to my phone in Windows without them. 

So, I pretty much have to put the installer in Windows from Linux, so I can run it, have internet in Windows and not get fired tomorrow.

I have $0, so picking up (or borrowing) something I can use to talk between the two computers is not an option.

But in Ubuntu, I do not see my Windows partition. It's not in media and it's not in mnt.

What can I do to get a damn file over to Windows?
[I][B]
Note in bold and italic to show that it's important: NTFS-Config only shows my Ubuntu drive, it seems.

EDIT: Oh boy, I screwed up.

[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[/B][/I]

---

### Post by holiday on 2010-10-18
> **Leopardson said:**
> So, I've got a ridiculously complicated problem.

I have a desktop, a cellphone. I do NOT HAVE a disk drive, a USB stick or anything of the sort.

The desktop has two operating systems on a single hard drive: Ubuntu 10.04 and Windows 7.
I need to get internet access in Windows 7.

The cellphone is a Galaxy S Vibrant, and is tethered so that I can connect to the internet through it.
In Ubuntu, the tether is automatically supported. I just shove a USB cable between the cellphone and the phone and I've got internet in Linux.
But in Windows, the tether needs drivers. I can't connect to my phone in Windows without them. 

So, I pretty much have to put the installer in Windows from Linux, so I can run it, have internet in Windows and not get fired tomorrow.

I have $0, so picking up (or borrowing) something I can use to talk between the two computers is not an option.

But in Ubuntu, I do not see my Windows partition. It's not in media and it's not in mnt.

What can I do to get a damn file over to Windows?

What comes up in Places - on the main menu. My windows partition comes up there.

---

### Post by Leopardson on 2010-10-18
Computer
14gb Filesystem (Cellphone)
2gb Filesystem (Cellphone SD card, and no, I don't have an SD port in my desktop)
Disc (DVD-R, no longer useful.)

---

### Post by holiday on 2010-10-18
You're trying to get a file into Windows? Is that right?

Upload it to Google Docs, boot into Windows and pull the file down.

---

### Post by Leopardson on 2010-10-18
If I had internet access, I wouldn't be doing this. ](*,)

---

### Post by holiday on 2010-10-18
> **Leopardson said:**
> If I had internet access, I wouldn't be doing this. ](*,)

Ouch! So sorry, my Bad.

You have internet access in Ubuntu? You can still put it to Google Docs, and pull it down in the morning from your work machine? Is that possible?

---

### Post by Leopardson on 2010-10-18
There won't be a work machine tomorrow if I don't have this to her by 12:00am.

---

### Post by nlneilson on 2010-10-18
Places>Computer>File System>host

This works, Ubuntu is installed under Win.

If you partitioned the HD and installed I have no idea, had problems doing it that way.

I have a data directory (8~10 GB) and an app (graphics based on NASA WWJ) that runs on Win and 10.04, can access that data (read, write) from either OS.

---

### Post by blueridgedog on 2010-10-18
How did you install Ubuntu?  Wubi or regular install?

What is the output of the following commands?:

```
sudo fdisk -l
```

```
mount
```

Also, is the cellular data storage available when you plug the phone into windows or is a driver needed for that as well?  ie...could you copy the files you need to the phone?

---

### Post by Leopardson on 2010-10-18
I'm sure that would work, if I could still boot. [http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)

---

### Post by dtfinch on 2010-10-18
Does the partition show up when you run "sudo fdisk -l"?

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

There's also [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) , but the manual solution they suggest if ntfs-config doesn't work is unnecessarily long.

It is odd that it didn't show up in Places. If Windows did not shut down cleanly, the partition would be marked as unclean which would cause it to not mount, and you'd have to either boot back into Windows for the automatic disk check or run ntfsfix on it in Ubuntu before mounting it. Or mounting with the "ro" option for read-only might work.

---

### Post by Leopardson on 2010-10-18
[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)

Thanks for all the help, but:
[B][SIZE=5]UBUNTU DOES NOT BOOT ANY MORE :(

[http://ubuntuforums.org/showthread.php?t=1600367](http://ubuntuforums.org/showthread.php?t=1600367)
[/SIZE][/B]

---

