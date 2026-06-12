---
title: "Where to mount"
date: 2011-02-24
forum: General Help
---

### Post by Norwegian-Blue on 2011-02-24
Hi,

I am quite new to unix/linux and was wonderind what the convention was for mounting external drives.

I have a NAS box, initially I just mounted the root of the NAS box to /mnt/nas and then symlinked any sub directory I wanted access to to a particular place. For example

the Pictures directory on the NAS box was symlinked from /mnt/Pictures to /home/Ian/Pictures

However I now see that I would like some directories to be readonly. So I mounted made two mounts

NAS                                     Local
/Pictures/Old (readonly)        /mnt/Pictures/Old
/Pictures/New                       /mnt/Pictures/Current

And then symlinked these to /home/Ian/Pictures/Old and  /home/Ian/Pictures/Current.

but then I thought, why don't I just mount direct to the home folder rather than using symlinks:

NAS                                     Local
/Pictures/Old (readonly)        /home/Ian/Pictures/Old
/Pictures/New                       /home/Ian/Pictures/Current

But then, a icon of a disk named OLD appeared on my desktop !!

My questions are:

1) Is it ok to directly mount to home ? or should all mounts go to /mnt/.... ?
2) Why is this icon appearing on my desktop and how can I get rid of it ?

Many thanks
Ian

---

### Post by Smart Viking on 2011-02-24
It is ok to mount anywhere in the file hirarchy.
I don't know why there's an icon there.

---

### Post by seawolf167 on 2011-02-24
> **Norwegian-Blue said:**
> 1) Is it ok to directly mount to home ? or should all mounts go to /mnt/.... ?
2) Why is this icon appearing on my desktop and how can I get rid of it ?


[LIST=1]
[*]You can mount anywhere, typically /mnt/ is used, but you can mount anywhere
[*]The icon could be appearing because Ubuntu is thinking of this as a shared folder (i.e. if you connect to a shared folder or drive [at least in 9.04->10.04] it automatically places a shortcut on the Desktop).
[/LIST]
Edit: forgot to mention that even my "extra" internal drives mounted via /etc/fstab get an icon automatically placed on the desktop in 10.04

---

### Post by wiggly81 on 2011-02-24
the icon can be removed in gconf-editor

press Alt+F2 type in gconf-editor
navigate to 
apps > nautilus > desktop

it will be volumes visible option im im thinking about the correct icon

---

### Post by Norwegian-Blue on 2011-02-26
Thanks for all the answers.

It is a bit strange that when mounted to /mnt/.... that Ubuntu does not add an icon on the desktop but then mounting anywhere else it does.

The gconf-editor tip worked. But it is a shame that it is a "all of nothing" option. I quite like that a icon appears then I add an external USB disk, but I dont want it for all my mounts. 

Regards
Ian

---

### Post by Morbius1 on 2011-02-26
Anything mounted to your /home/xxx folder or in /media will produce a mount icon.

Anything mounted to /mnt or off "/" itself will not.

I don't know why that is.

---

