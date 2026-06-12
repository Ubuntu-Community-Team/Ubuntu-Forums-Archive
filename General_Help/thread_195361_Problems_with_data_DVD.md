---
title: "Problems with data DVD"
date: 2006-06-12
forum: General Help
---

### Post by Hoffmann on 2006-06-12
Hello:

I am trying to read a (data) DVD, but I am having (premission) problems. Could anyone, please, help me on that?
Thanks!

---

### Post by deadgobby on 2006-06-12
[QUOTE=Hoffmann]Hello:

I am trying to read a (data) DVD, but I am having (premission) problems. Could anyone, please, help me on that?
Thanks![/QUOTE]
Is that after you install the Codecs?

---

### Post by scxtt on 2006-06-12
check the permissions on where ever the dvd drive is mounted, for example:
```
$:> ll /media
total 8.0K
drwxr-xr-x 22 root root 4.0K 2006-06-04 04:26 breezy
lrwxrwxrwx  1 root root    6 2006-06-09 03:05 cdrom -> cdrom0
drwxr-xr-x  2 root root 4.0K 2006-06-09 03:05 cdrom0
```as you can see, both 'group' and 'other' have read/execute permissions for everything in /media ... if all else fails, try doing whatever you want to do using sudo ...

NOTE: my dvd-rom is mounted cdrom/cdrom0, both of which are references to /dev/hdb (which is my dvd-rom's device address) ...

---

### Post by Hoffmann on 2006-06-12
[QUOTE=scxtt]check the permissions on where ever the dvd drive is mounted, for example:
```
$:> ll /media
total 8.0K
drwxr-xr-x 22 root root 4.0K 2006-06-04 04:26 breezy
lrwxrwxrwx  1 root root    6 2006-06-09 03:05 cdrom -> cdrom0
drwxr-xr-x  2 root root 4.0K 2006-06-09 03:05 cdrom0
```as you can see, both 'group' and 'other' have read/execute permissions for everything in /media ... if all else fails, try doing whatever you want to do using sudo ...

NOTE: my dvd-rom is mounted cdrom/cdrom0, both of which are references to /dev/hdb (which is my dvd-rom's device address) ...[/QUOTE]

I have
> total 16
lrwxrwxrwx  1 root root    6 2006-05-29 15:30 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-05-29 15:30 cdrom0
drwxr-xr-x  2 root root 4096 2006-05-29 15:30 cdrom1
drwxr-xr-x 12 root root 4096 1969-12-31 18:00 sda1
drwxr-xr-x  2 root root 4096 2006-05-29 15:30 sda2
 
and  as soon as I insert my data CD I have:
> total 18
lrwxrwxrwx  1 root root    6 2006-05-29 15:30 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-05-29 15:30 cdrom0
drwxr-xr-x  2 root root 4096 2006-05-29 15:30 cdrom1
dr-xr-x--- 33 root root 1804 2006-05-13 12:00 dvdrecorder
drwxr-xr-x 12 root root 4096 1969-12-31 18:00 sda1
drwxr-xr-x  2 root root 4096 2006-05-29 15:30 sda2

Can I hear from you again? I mean, how can I see where is my DVD mounted, in order to change the permission? Note that I am having no problem with CDs.

---

