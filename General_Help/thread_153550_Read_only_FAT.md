---
title: "Read only FAT"
date: 2006-04-01
forum: General Help
---

### Post by Ramses de Norre on 2006-04-01
How would you change the line in fstab for a fat partition so that it is mounted read only for all users exept of root?
My current line is ```
/dev/hda1       /mnt/hda1  vfat iocharset=utf8,umask=000 0 0

``` which makes the partition rw for everyone.

---

### Post by Sutekh on 2006-04-01
umask removes permissions from a full permissions state, like the Unix style 777 permissions.

So umask=000 would be a Unix mask of 777 - full access, as you know

If you want full access for root (the owner) - 7,  and read access only for everyone else - 4, then the umask should be equal to **003**.  This would be like 774 permissions in Unix.

So the first number takes nothing away from the owner and owning group (both root), but takes away 3 (write and execute access) from the everyone else.



All this taken from the Gentoo Wiki
> umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

* character '0': Indicates that this is an octal number, not decimal.
* first digit: owner user permissions
* second digit: owner group permissions
* third digit: world permissions (every other user on the system)

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * -
2 | * - *
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: 

---

### Post by Ramses de Norre on 2006-04-01
So umask 033 would make it rwx to the owner of the mount point and ro for everyone else, Thanks ;)

---

### Post by Sutekh on 2006-04-01
033 would make it rwx for the owner only and read (but no execute) for everyone else, yes.

Once you get the hang of it that table above is pretty useful.

---

### Post by Ramses de Norre on 2006-04-01
```
/dev/hda1       /mnt/hda1  vfat iocharset=utf8,umask=0022 0 0
```
```
/dev/hda1       /mnt/hda1  vfat iocharset=utf8,umask=022 0 0
```
I've tried those two, and both give r-xr-xr-x instead of rwxr-xr-x
Am I getting it wrong?

---

### Post by Sutekh on 2006-04-01
Oops I forgot to mention the umask should be **4** numbers.  

The first being
> * character '0': Indicates that this is an octal number, not decimal.
followed by the three other digits for the permissions

Try umask=**0**022

---

### Post by Ramses de Norre on 2006-04-01
That's why I tried that first line, but it gave the same permissions.. (r-xr-xr-x)

---

### Post by Sutekh on 2006-04-01
I'm going blind...

:)


Edit: Okay I just tried it on my box, and I have rwxr-xr-x , when I use 0022 and 022.  So you are doing it right, something else is happening

---

### Post by Ramses de Norre on 2006-04-01
Shouldn't umask overwrite the permissions of the files? The mount point has the right permissions, so as quite a lot of the files in it.
But some still have the wrong ones.

---

### Post by Sutekh on 2006-04-01
Sorry I was wrong it wasn't working before for me. I was looking at the wrong device.

Okay try unmounting the partition, then make the changes to the umask, save the fstab then mount the partition again.

This is what I did
```
sudo umount /dev/hda5
```
Then changed the umask to 022
```
sudo mount /dev/hda5
``` and the permissions were changed.

---

### Post by Ramses de Norre on 2006-04-01
I saved the fstab and unmounted/remounted it allready, still the same permissions.

---

### Post by Sutekh on 2006-04-01
Then I am so confused, I haven't had a problem trying it here.  The umask should change the permissions of the mount folder and all the files when the partition is mounted.  

When I messed around with the umask here, It didn't work when I tried 'mount -a', but did work when I 'umount/mount' the partition.

---

### Post by Ramses de Norre on 2006-04-01
That's what I did too.. Changed the fstab with vi, then sudo umount /dev/hda1 && sudo mount /dev/hda1

---

