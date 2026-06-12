---
title: "Cannot unmount volume"
date: 2009-09-27
forum: General Help
---

### Post by SoftwareExplorer on 2009-09-27
I get the following error when ever I try to burn a CD. I also think it happens when I tell the computer to eject the CD.

[SIZE="3"]Cannot unmount volume[/SIZE]
Cannot unmount the volume 'Ubuntu 9.10 amd64'.

Details:
 umount: only marta can unmount /dev/
 scd0 from /media/cdrom0
I don't know if this will help:
```
ls -l
total 30
lrwxrwxrwx  1 root root    6 2009-03-19 22:51 cdrom -> cdrom0
dr-xr-xr-x 10 root root 2048 2009-09-16 19:08 cdrom0
drwxr-xr-x  2 root root 4096 2009-08-08 20:33 data
drwxrwxrwx  8 root root 4096 2009-09-23 06:17 Data-500
drwxr-xr-x 21 root root 4096 2009-09-27 06:52 disk
lrwxrwxrwx  1 root root    7 2009-03-19 22:51 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2009-03-19 22:51 floppy0
drwxr-xr-x  2 root root 4096 2009-09-18 06:19 sda1-back
drwxr-xr-x 21 root root 4096 2009-09-27 06:52 sda2-back
drwxr-xr-x  2 root root 4096 2009-09-18 17:58 sda6-back

```
I imagine it is a permissions error, but I could be wrong.
How can I fix it?
Thanks in Advance

---

### Post by t0p on 2009-09-27
Are you username marta?  If not, you need to give your username permission to use the cd drive, under **System > Administration > Users & Groups**.

---

### Post by SoftwareExplorer on 2009-09-27
No, I'm 'bjorn'. My user has everything checked under the user privileges tab.

---

### Post by StuartN on 2009-09-27
> **SoftwareExplorer said:**
> No, I'm 'bjorn'.

It looks like Marta will have to log in and eject the CD, then you can take possession of the drive.

---

### Post by SoftwareExplorer on 2009-09-27
I plugged in a usb drive and it was mounted under disk-1.
When I looked at user permissions, it was automatically owned by the user marta, and the group root. How did this happen? The last time I ls'ed /media it didn't list that folder, and now marta automatically owns it when it seems to have been created on the fly.

Also, this is a recurring problem, even if I get the cd ejected with nautilus running as root, the problem happens the next time.

---

### Post by zman58 on 2009-09-27
> **SoftwareExplorer said:**
> I plugged in a usb drive and it was mounted under disk-1.
When I looked at user permissions, it was automatically owned by the user marta, and the group root. 

That sounds like a problem. What is owned by marta? The files on the device or the actual device mount point /media/disk-1/. ?

If you plug in the drive while you are using the desktop, and no one else has a desktop up, then the mountpoint should be owned by you "bjorn".

Is it possible that you are on a secondary desktop login and marta is actually logged in on another desktop on the same machine??

Go to a command prompt and type:
who

Does it show only you as being logged in?

---

### Post by SoftwareExplorer on 2009-09-28
I'm logged in multiple times, with the users marta and annika logged in once each.
```

marta    tty12        2009-09-27 13:31 (:0)
bjorn    tty9         2009-09-24 20:10 (:20)
bjorn    pts/0        2009-09-25 06:32 (:20.0)
bjorn    pts/1        2009-09-25 06:51 (:20.0)
bjorn    pts/2        2009-09-25 21:46 (bjorn-backup.local)
annika   tty11        2009-09-25 22:03 (:21)
bjorn    pts/3        2009-09-27 20:19 (:20.0)
bjorn    pts/4        2009-09-26 15:11 (:20.0)
bjorn    pts/6        2009-09-27 07:11 (:20.0)
bjorn    pts/7        2009-09-27 07:12 (:20.0)

```
As far as what marta owns, I figured out the disk-1 permissions by doing ls -l /media. I think that would mean marta owns the mount point folder, not the drive?

As far as the mount point ownership, shouldn't root own it, but it should be readable and executable by everyone right? It seems that way on another computer where cdrom1 mount point is owned by root, has the root group and has  drwrx-xr-x permissions.

Thanks for the help so far. :)

---

### Post by zman58 on 2009-09-30
Interesting problem. I do not see the same on my Ubuntu 8.04 system. If I have another user logged into a tty, then plug in USB thumbdrive while my desktop is active then I own mount point like so:

kzahorec@zpresario2:~$ ls -l /media/
total 24
lrwxrwxrwx 1 root     root     6 2009-02-20 08:35 cdrom -> cdrom0
drwxr-xr-x 2 root     root  4096 2009-02-20 08:35 cdrom0
drwx------ 7 kzahorec root 16384 1969-12-31 19:00 disk
lrwxrwxrwx 1 root     root     7 2009-02-20 08:35 floppy -> floppy0
drwxr-xr-x 2 root     root  4096 2009-02-20 08:35 floppy0
kzahorec@zpresario2:~$ ls /media/disk/
download  dyne  images  kzahorec  michael

Notice group for /media/disk mount point is root.
Since I own it, I can unmount it.

As a test: If marta and annika are logged out when you plug it in then would you own it?

I do notice that if the desktop is not active at the time it is plugged in (i.e. full screen tty on other account is active), then the USB thumbdrive will not automount.

So my next question is: Is your desktop active and forward when you actually plug in the drive?

---

### Post by SoftwareExplorer on 2009-10-02
When I tried plugging in the usb drive when I was the only one logged in, root was the owner and group of the mountpoint. To make sure everyone was logged off, I restarted. Now it seems like the CD is behaving, because it let me eject it even though marta and annika have logged in since I restarted. So I think the problem solved itself. 

Thanks for your help zman58, StuartN, and t0p. :)

---

