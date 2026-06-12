---
title: "&quot;permission denied&quot; but permissions are good"
date: 2010-09-18
forum: General Help
---

### Post by UncleBoarder on 2010-09-18
What am I missing?  listing 1 below, allows me to execute ./vim.tiny   But listing 2 does not.  They appear the same to me...

I also tried a full path execution.  I get "bash: /mnt/shared/Ubuntu/usr/bin/vim.tiny: Permission denied"

Attempted with and without "sudo"

Listing 1:

[FONT=Fixedsys]root@Ubuntu:/usr/bin# ls -l v*
lrwxrwxrwx 1 root root      4 2010-09-05 12:03 vboxwebsrv -> VBox
lrwxrwxrwx 1 root root     20 2010-09-04 22:16 vi -> /etc/alternatives/vi
lrwxrwxrwx 1 root root     22 2010-09-04 22:16 view -> /etc/alternatives/view
-rwxr-xr-x 1 root root  23872 2010-03-22 16:28 viewres
**-rwxr-xr-x 1 root root 754744 2010-04-16 09:33 vim.tiny**
-rwxr-xr-x 1 root root 312208 2010-06-25 01:06 vinagre
-rwxr-xr-x 1 root root  10560 2010-04-09 04:02 vino-passwd
-rwxr-xr-x 1 root root  61336 2010-04-09 04:02 vino-preferences
-rwxr-xr-x 1 root root   6264 2010-04-22 11:14 vmmouse_detect
-rwxr-xr-x 1 root root  22832 2009-12-16 14:34 vmstat
-rwxr-xr-x 1 root root   6328 2009-11-10 03:07 volname[/FONT]

Listing 2:

[FONT=Fixedsys]root@Ubuntu:/mnt/shared/Ubuntu/usr/bin# ls -l v*
lrwxrwxrwx 1 root root      4 2010-09-05 12:03 vboxwebsrv -> VBox
lrwxrwxrwx 1 root root     20 2010-09-04 22:16 vi -> /etc/alternatives/vi
lrwxrwxrwx 1 root root     22 2010-09-04 22:16 view -> /etc/alternatives/view
-rwxr-xr-x 1 root root  23872 2010-03-22 16:28 viewres
**-rwxr-xr-x 1 root root 754744 2010-04-16 09:33 vim.tiny**
-rwxr-xr-x 1 root root 312208 2010-06-25 01:06 vinagre
-rwxr-xr-x 1 root root  10560 2010-04-09 04:02 vino-passwd
-rwxr-xr-x 1 root root  61336 2010-04-09 04:02 vino-preferences
-rwxr-xr-x 1 root root   6264 2010-04-22 11:14 vmmouse_detect
-rwxr-xr-x 1 root root  22832 2009-12-16 14:34 vmstat
-rwxr-xr-x 1 root root   6328 2009-11-10 03:07 volname
[/FONT]

---

### Post by sisco311 on 2010-09-18
My guess is that /mnt/shared/Ubuntu/ is mounted with the noexec option. 

But, what exactly are you trying to accomplish?

---

### Post by Iowan on 2010-09-18
How is the directory mounted (fstab)? It's possible that the mount itself needs to have permissions adjusted.

---

### Post by UncleBoarder on 2010-09-18
Mostly I'm trying to learn about Ubuntu and how moving file structures and mounting functions.  But currently I'm attempting to move the /usr directory to another volume.

Here's my fstab mount for the volume I'm trying to move /usr to...

# My shared volume /dev/sdb1
UUID=e0352916-43a0-431c-bd64-08a5f3182543  /mnt/shared              ext3  defaults,user,errors=remount-ro    0  0  

My next step would be to create an fstab entry for the new /usr path but first it needs to work locally.  That's the point of my question.  How do I correct my permission problem?

---

### Post by UncleBoarder on 2010-09-18
OH... I see the noexec IS listed when I look at the mounted status.  I guess that's a "default"?

That was it!  

I swear this worked when it was mounted in /media.  I'll check it and post in another thread.

Thanks!

---

### Post by sisco311 on 2010-09-18
> **UncleBoarder said:**
> Mostly I'm trying to learn about Ubuntu and how moving file structures and mounting functions.  But currently I'm attempting to move the /usr directory to another volume.

Here's my fstab mount for the volume I'm trying to move /usr to...

# My shared volume /dev/sdb1
UUID=e0352916-43a0-431c-bd64-08a5f3182543  /mnt/shared              ext3  defaults,user,errors=remount-ro    0  0  

My next step would be to create an fstab entry for the new /usr path but first it needs to work locally.  That's the point of my question.  How do I correct my permission problem?

According to the man page (**man mount**) the **user** mount option implies the **noexec, nosuid and nodev options (unless overridden by subsequent options)**. So, remove **user** (oh and errors=remount-ro) from the mount options... and try again.

---

### Post by UncleBoarder on 2010-09-19
That was it.  The "user" option was changing it back to "noexec".

Thanks!

---

