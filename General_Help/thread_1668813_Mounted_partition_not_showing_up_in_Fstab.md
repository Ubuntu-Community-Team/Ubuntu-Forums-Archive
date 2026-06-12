---
title: "Mounted partition not showing up in Fstab"
date: 2011-01-16
forum: General Help
---

### Post by Lordmort on 2011-01-16
Hi, I'm totally new with linux and Ubuntu. I've just installed 10.10 yesterday and since then it's been an uphill struggle :)

These forums has helped me out quite a bit already so I hope you can continue doing it with this problem I have.

I got a single drive where the bootpartition is ext4 and the other "storage" partition is a remenant from a windows 7 installation I had, with NTFS. Decided I wanted to give Ubuntu a try! :D

Now i've run into permission trouble though, mainly because I wanted to set up an FTP server (oh what a struggle THAT's been, I have some stories... :) ). I've done a "mount --bind" so that I can reach different resources directly from my chroot. It turns out though that the mounted partition isn't giving anyone except the owner (me) permission to see the resources. FTPing into the server gives the mount points but gives a 550 error and can't list anything inside of them. 
It works perfectly for me just running it at the prompt or using the mount points directly in the Ubuntu GUI though (since I'm the owner/admin/whatever).

My intended solution that I've found was that people with NTFS drives did a few magic tricks with the line of text in Fstab so they could access their NTFS drives. Problem for me is that my sda3 mount isn't showing up at all in fstab, even though fstab is supposed to (as far as I know) show all mounted devices on there. 

All the while, I have my sda3 totally accessible from /media/Storage/. Any pointers as to why this is?

After I installed Ubuntu, I just mounted the sda3 with the Disk Utility from System->Administation and didn't think much of it afterwards until now.

What's the best course of action here? remount the ntfs partiton using fstab? Convert the ntfs partition into an ext4? I have a lot of data on there I want to keep as well.

Getting a bit longwinded here, hope you can shed some light on this issue.

Cheers!

/ Thomas

---

### Post by Lordmort on 2011-01-17
Anyone? Why isn't my NTFS partition showing up in Fstab? How should I go about giving people rights to it?

---

### Post by Morbius1 on 2011-01-17
Ubuntu will automatically mount non system disks that aren't specified in fstab at /media/LABEL or /media/UUID.

If you want to automatically mount the partition with your own permissions specified then I would follow these steps:

[1] Unmount the partition if it's already mounted:
```
sudo umount /media/Storage
```[2] Create a permanent mount point at that location:
```
sudo mkdir /media/Storage
```[3] Add a line to /etc/fstab - I'm basing this on the info you provided in your post:
```
/dev/sda3 /media/Storage ntfs defaults,nls=utf8,umask=0000,uid=1000 0 0
```[4] Save fstab and in a terminal run this command:
```
sudo mount -a
```If there are any errors "mount -a" will display them. If not it will mount your new partition.

---

### Post by dandnsmith on 2011-01-17
When you mount it with Disk Utility, it probably shows up in /etc/mtab (which keeps a list of mounted partitions).

I don't know what the magic fix is to fstab, as I tried it myself, based on such an entry, and got an error which I've never gone back to resolve.

If you try the conversion, you could lose the lot (a possibility) - copy or backup the data (external drive or CD/DVD), format the partition and then restore the data would be a safer way to do it.

* beaten to it while composing the post*

---

### Post by Lordmort on 2011-01-17
Works like a charm! I've been thinking some kind of mounting had to be done in fstab, but I was really unsure of what uid, gid and umask values I should use. Thanks a bunch!

---

