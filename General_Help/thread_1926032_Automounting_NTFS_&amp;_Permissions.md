---
title: "Automounting NTFS &amp; Permissions"
date: 2012-02-15
forum: General Help
---

### Post by astrobob.tk on 2012-02-15
Hello there,

I recently add one of my NTFS partitions to the fstab file so that it automounts:

```
UUID=************    /media/***    ntfs    defaults,nls=utf8,umask=0222    0    0
```I followed this thread: [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

This is great but I cannot unmount the partition unless I am the root (not a sudoer) & I do not have permission to add (copy/cut & paste) or move new files into or out of the partition.

I just read about the permissions thing: [http://ubuntuforums.org/showthread.php?t=1355601](http://ubuntuforums.org/showthread.php?t=1355601)

My question is: can't I change the permissions unless it is a Unix/Linux type format?

Any suggestions?

Note: I share this partition with my Win system.

---

### Post by Leppie on 2012-02-15
> **astrobob.tk said:**
> 
This is great but I cannot unmount the partition unless I am the root (not a sudoer) & I do not have permission to add (copy/cut & paste) or move new files into or out of the partition.
change the line to something like this:
```
UUID=************    /media/***    ntfs    defaults    0    0
```> **astrobob.tk said:**
> 
My question is: can't I change the permissions unless it is a Unix/Linux type format?
no, ntfs does not support file permissions. i believe that  windows file permissions are stored in policies.

---

### Post by astrobob.tk on 2012-02-15
> **Leppie said:**
> change the line to something like this:
```
UUID=************    /media/***    ntfs    defaults    0    0
```

what exactly does this do? any negatives?

---

### Post by Leppie on 2012-02-15
it will just mount the ntfs partition with all the defaults, e.g. no file permissions.
the file permissions were blocking you access from the linux side, though technically anyone could write to an ntfs partition from linux.

there's no negative sides, unless you find a bug in the ntfs driver.

---

### Post by astrobob.tk on 2012-02-15
> **Leppie said:**
> it will just mount the ntfs partition with all the defaults, e.g. no file permissions.
the file permissions were blocking you access from the linux side, though technically anyone could write to an ntfs partition from linux.

there's no negative sides, unless you find a bug in the ntfs driver.


:D thanks.that worked

---

### Post by Leppie on 2012-02-15
glad it to hear

---

### Post by astrobob.tk on 2012-02-17
> **Leppie said:**
> glad it to hear

hey Leppie,

I guess im facing a problem. I had some movies moved to this partition &now every time I play any of them in Gnome Mplayer I get the following error

[IMG]http://img546.imageshack.us/img546/9775/gnomemplayererror001.jpg[/IMG]

any idea about this ?

update: as a matter of fact it its a Gnome Mplayer error. I checked the following & followed the 2nd answer to stop the error: [http://askubuntu.com/questions/13487/gnome-mplayer-failed-to-open-vdpau-backend-libvdpau-nvidia-so-error](http://askubuntu.com/questions/13487/gnome-mplayer-failed-to-open-vdpau-backend-libvdpau-nvidia-so-error)

---

### Post by astrobob.tk on 2012-10-18
I have this new issue with automounting but with an ext4 partition.

I'd like to automount the partition & so I added the following line to fstab:

```
UUID=<uuid> /media/data     ext4    defaults        0       2

```

I made the directory /media/data before that too.

At boot I'm getting the following error:
```
Serious errors were found while checking the disk drive /media/data
```

& promoted to Ignore, Skip, or manually mount.

What seems to be the problem?

thanks

---

### Post by Wim Sturkenboom on 2012-10-18
That your partition is corrupted. Are you sure it's ext4 and formatted as such?

And please start your own thread, this oldish one is about ntfs, not about ext4. You're missing out on people that might be able to help you because the title states 'ntfs'.

---

### Post by astrobob.tk on 2012-10-18
> **Wim Sturkenboom said:**
> That your partition is corrupted. Are you sure it's ext4 and formatted as such?

And please start your own thread, this oldish one is about ntfs, not about ext4. You're missing out on people that might be able to help you because the title states 'ntfs'.

I am sorry about that; you're right. I posted this thread before about NTFS,

Here's the  new thread: [http://ubuntuforums.org/showthread.php?p=12303046](http://ubuntuforums.org/showthread.php?p=12303046)

thanks

---

