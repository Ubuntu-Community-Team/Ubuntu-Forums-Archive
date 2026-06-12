---
title: "The amazing fable of the ghost files on my external HDD..."
date: 2011-12-05
forum: General Help
---

### Post by fmmarzoa on 2011-12-05
Hi there,

I'm facing problems with an iomega external HDD that has work fine until now, being ext3 partition and used within an Ubuntu 10.04 distribution.

After deleting all its content by mistake during the install of an Ubutun 11.10, I've created an ext4 partition and copied them some files.

Since that, paranormal activity related to this disk has been increased.

At first, when I plugged the HDD, Ubuntu mounts in two points:

/media/iomega
/media/iomega_

And by default, opens the second one, where there was only a lost+found directory. But putting in nautilus /media/iomega (using ctrl+l) as location, the real contents of the hard disk was there.

Now it just mounts /media/iomega, and there's nothing there but lost+found void directory. Sure? Well, not actually.

fran@durruti:~$ sudo ls -lRa /media/iomega
/media/iomega:
total 24
drwxr-xr-x 3 root root  4096 2011-12-03 19:45 .
drwxr-xr-x 3 root root  4096 2011-12-06 00:12 ..
drwx------ 2 root root 16384 2011-12-03 19:45 lost+found

/media/iomega/lost+found:
total 20
drwx------ 2 root root 16384 2011-12-03 19:45 .
drwxr-xr-x 3 root root  4096 2011-12-03 19:45 ..

But look at this:

fran@durruti:~$ df -h /media/iomega
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  198M  435G   1% /media/iomega

Where are those 198 megabytes??? O_o

In fact, there should be a Picture and Video directories in the disk, with some -you guess right- pictures and videos. But they aren't. :-?

I've backup of everything in another external harddisk, so I'll recover it ASAP. Just wonder if someone has an explanation for this behaviour... ????

Best regards,

---

### Post by carranty on 2011-12-05
First, can you please open an terminal and type

```
df -h
```

Then, please type

```
du -h /media/iomega
```

```
and du -h /media/iomega_
```

Please post the command + output to the thread.

---

### Post by fmmarzoa on 2011-12-06
Hi,

As I told, /media/iomega_ does not exists anymore.

I'm thinking now that for some reason there may be a /media/iomega directory created on my FS, so when the system wants to mount /media/iomega could not do it and therefore it mounts into /media/iomega_ instead.

So, I think I copied my files into the directory /media/iomega on my main HDD instead of the iomega one, and that's the reason because they are not there anymore.

The 200 Mbytes used on the usb HDD may be those occupied by ext4 itself, you know, that space reserved for root, and inodes and so...

Best regards,

---

