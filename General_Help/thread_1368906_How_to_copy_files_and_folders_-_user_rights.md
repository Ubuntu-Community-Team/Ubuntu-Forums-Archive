---
title: "How to copy files and folders - user rights"
date: 2009-12-31
forum: General Help
---

### Post by Odense on 2009-12-31
My Lenovo s10 netbook have stopped booting - seems some files have been corrupted - so I would like to copy the "home" directory to an external HD.

When I try this after booting on a "Live CD on a USB Stick" I are informed I am not allowed to copy the files.

I tried to use "sudo nautilus" in a terminal window - but that was not really accepted - how do I copy the files ?

---

### Post by ajgreeny on 2009-12-31
Two possible ways, well more actually, but two most obvious ones.

1.  Try again using ```
gksudo nautilus
``` in the live CD.  This will open a nautilus window with root privileges, and should allow you to copy the files to your external.  **sudo** is for command line applications only, for gui apps it should always be **gksudo**, though some simpler gui apps will work with sudo.

2.  In the live CD make a new user with your same username as the installed version, and with admin permissions, and you should be able to move the files simply as the new user.

However, what seems to be the problem with booting?  Tell us what is going on and it may well be possible to put it right and stop you needing to reinstall, if that is what you intend to do.

---

### Post by Odense on 2009-12-31
Firstly thanks - I tried on a single file after using gksudo and it seems to work :)

You are right - I would prefer to repair the boot files if possible - so here is the specifics:

When I try to boot the netbook from the harddisk it starts a filesystem check and gets to 70 % and stops moving.

After a long time I get this message:
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@morten-laptop:~#

---

### Post by danastasio on 2009-12-31
When you get to that shell, try running

```
e2fsk -fvP
```

This will run a file system check and correct any errors. It sounds like you have a corrupted file system.

---

### Post by Odense on 2009-12-31
Thanks - I will try that - but after I finish copying all my files from the netbook to an USB HD

Someone suggested using "Gparted" for a smilar problem (se below) - would that work too:

"You can fix it by booting your Ubuntu CD and opening 'System', 'Administration', GParted', right-click on your Ubuntu partition and click 'check'.
Confirm in two different 'Apply' buttons.
Wait a few minutes while the file system check is runnning.
When it's finished, reboot into your operating system, it should be all fixed."

---

### Post by Odense on 2009-12-31
> **danastasio said:**
> When you get to that shell, try running

```
e2fsk -fvP
```This will run a file system check and correct any errors. It sounds like you have a corrupted file system.

My netbook suggests e2fsck instead - but even when using that with the switches -fvp (which I understand) nothing still happens - maybe I have to pick something with regards to superblocks and blocksize - but I don't know what to pick ?

I am naturally still curious about the missing switches (argument ?) to use with e2fsck -fvp but it seem that using Gparted to check and fix the drive worked :)

---

### Post by Odense on 2010-01-02
> **Odense said:**
> 
I am naturally still curious about the missing switches (argument ?) to use with e2fsck -fvp but it seem that using Gparted to check and fix the drive worked :)

So - anybody know how I get the e2fsck to actually run - I just get a usage page with a list of switches when I try to run it ?

---

### Post by Zteam on 2010-01-02
> **Odense said:**
> So - anybody know how I get the e2fsck to actually run - I just get a usage page with a list of switches when I try to run it ?

I think you have to tell it which partition you want it to check

So first of all you have to find your / partition

So run this:

```
sudo df
```

This will give you a list of your partitions, one should be mounted on
/ as you can see all your partitions have a name like /dev/sda1

**Here is an example**

```
Filesystem	Size	Used	Avail	Use%	Mounted on
/dev/hda2 	28G 	7.6G 	19G	29%	/
tmpfs 	252M 	0	252M	0%	/lib/init/rw
tmpfs	252M	0	252M	0%	/dev/shm
/dev/hda1	464M 	37M	403M 	9% 	/boot
/dev/hda3	8.3G	429M 	7.5G	6%	/var
nfs6:/home 	520G	461G	60G	89%	/home
mirrors:/mirrors	1.4T	1.1T	233G	83% 	/mirrors
/dev/mapper/big-phat  	77G	36G	42G	46% 	/space
mailstore:/var/mail	9.9G	4.8G	4.7G 	51%	/var/mail
```

In the example above the partition we want e2fsck to check is /dev/hda2

So we just type:

```
sudo e2fsck -vfp /dev/hda2
```

---

### Post by Odense on 2010-01-03
Thanks - that is is - BUT the problem is that the partition that needs to be checked (with the dubious sectors) is the active partition - since the netbook only has one HD with one partition.

So it has to be done after booting on a Live CD or Live USB - there is no tols in Ubuntu to check it "on the fly" ?

---

