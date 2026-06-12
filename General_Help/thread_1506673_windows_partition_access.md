---
title: "windows partition access"
date: 2010-06-10
forum: General Help
---

### Post by fazio93 on 2010-06-10
I have a Vista/Ubuntu Dual Boot system on one hard drive. Vista has its own partition, and then Ubuntu has its own, plus the swap file it created. I want to restrict access to the Vista partition while in Ubuntu. It does not auto-mount the Vista partition, but it can easily be mounted by simply right clicking and pressing 'mount'. I opened my "fstab" file, but the only 2 entries listed are the Ubuntu install partition and the swap file partition for Ubuntu. I know it's not possible to completely hide it, because it will show in the 'Places' menu no matter what. What can I do for it to prompt for a password when trying to mount the vista partition. I have read of some people doing that, but do not know how.


Thanks

---

### Post by Morbius1 on 2010-06-10
> I know it's not possible to completely hide it, because it will show in  the 'Places' menu no matter what.Actually you can completely hide it if that's the ultimate goal.

For example if you add an entry into fstab that looks something like  this:

```
/dev/sda1 /Vista ntfs defaults,umask=777 0 0
```It won't show up under "Places" , it won't show up on the desktop, and with umask=777 nobody will be able to touch it.

You need to do some preliminary work though:

Find out the partition designation:
```
sudo blkid -c /dev/null
```Make the Vista mount point:
```
sudo mkdir /Vista
```

---

### Post by fazio93 on 2010-06-10
It worked like a charm. Thank you so much. :)

Just curious though, what did those commands actually do? I see the /Vista folder has a white "X" on it and it says "unreadable". The permission on it say that even root does not have access to list the files. How was this done?

Once again, thanks a bunch.

---

### Post by Morbius1 on 2010-06-10
umask represents the inverse permissions you want to assign to a windows filesystem ( doesn't work for linux filesystems  i.e., ext3, ext4, etc ). Each digit represents a class of user:

1st digit = owner
2nd digit = group
3rd digit = everyone else

A "1" turns off execute
A "2" turns off write
A "4" turns off read

The numbers are additive so a "7" ( 4+2+1 ) turns off everything.

In reality though root can still access the file even though it's got a "7" on it. Root can do anything it wants to do.

---

### Post by fazio93 on 2010-06-10
Ok, gotcha. Thank you so much.

Nick

---

### Post by happyendin21 on 2010-06-22
I am a noob to linux so i realize this may have been covered although I am not having any luck finding the information that I seek.  I have built a HTPC.  I dual boot windows 7 and a minimal install of ubuntu 9.10 to run xbmc.  I created a partition for my media outside of my windows and linux partitions.  I do not see access to this in my sources list in xbmc so I assume that it isn't being mounted by linux.  I have checked fdisk -l and see the partition that I speak of but I am not sure what to do from there to get linux to recognize that partition when I boot the computer.  If any one can point me in the right direction that would be great.  It being a minimal install I have no access to the ubuntu desktop only the terminal.  So terminal based commands would be helpful.  

Thanks in advance!

---

