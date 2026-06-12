---
title: "Drive Icons &amp; USB"
date: 2006-03-20
forum: General Help
---

### Post by barryp3uk on 2006-03-20
Hi everyone,

I'm a bit of a newbie curious to learn  about how Ubuntu handles my external USB HDD drive.

When I installed the drive was connected & switched on so it was mounted & as it is FAT32 it was read only. It was basically treated like any other HDD. OK with that &, to an extent, editing /etc/fstab/

It has six partitions so when all of them are mounted six icons appear on my desktop. Now I don't mean to be fussy but I quite like a clean desktop. Is there a way to remove *all* drive volume icons from there - maybe put them on a toolbar or something?

I experimented with removing all references to the external drive from /etc/fstab but some of the partitions were still mounted when booting up. I had to go into administration...disks to remove them & then I rebooted. Some still appeared. I rebooted with the drive switched off. Gone, of course.

I switched on the drive & all the partitions appeared again. Multiple versions of Nautilus also opened.

It seems that a mounted disk volume has lots of places [to which it is referred - for want of a better term] or from which it is controlled, not just the actual mount point.

I've read around about this but could anyone either point me to a good idiot's guide on the subject or explain a bit about the most convenient way of mounting & unmounting my external drive? Also as I mentioned earlier, doing this without lots of icons appearing on the desktop or multiple Nautili popping up?

Grateful for any advice or insight.

Cheers!
Barry.

---

### Post by IYY on 2006-03-20
Yes, it's possible to have no volume icons on the desktop. This can be done through the gconf-editor. I am not on my Ubuntu machine now so I don't remember exactly where that option is, but it should be very easy to find.

---

### Post by Ramses de Norre on 2006-03-20
```
gconf-editor /apps/nautilus/desktop
```
Uncheck volumes_visible.

---

### Post by barryp3uk on 2006-03-20
Hi folks,

Did that. The 3 volume icons for the partitions of hda, my windows fat volume, are still visible. Rebooted just in case, but they're still there.

Any ideas on my other questions?

1. Most convenient way of mounting & unmounting external drive.
2. Avoiding a Nautilus window for each partition popping up when the drive is recognised.

Cheers!

Barry.

---

### Post by Ramses de Norre on 2006-03-20
that option should handle all automaticaly created links, are you sure those remaining aren't self created symlinks?
What does ls -la ~/Desktop give?

---

### Post by barryp3uk on 2006-03-20
Hi  

I get
```

barry@upstairs:~$ ls -la ~/Desktop
total 8
drwxr-xr-x   2 barry barry 4096 2006-03-10 18:26 .
drwxr-xr-x  50 barry barry 4096 2006-03-20 19:13 ..

```

There are three icons - I don't know how this applies to them.

Cheers!

Barry.

---

### Post by barryp3uk on 2006-03-22
:confused:

---

### Post by Ramses de Norre on 2006-03-22
I've got those dotted ones too, I'll look for it later today as I'm forced to use windows now..

EDIT: just found this in another thread: ~/.nautilus/metafiles, maybe you can change things in there, but I'm not sure.

---

### Post by barryp3uk on 2006-03-22
Thanks.

Tried gedit:

"The file you tried to open is not a regular file".

Cheers!

B

---

### Post by Ramses de Norre on 2006-03-22
Tried gedit? On what? The path I gave you? Did you check the content? I don't now what's inside it, because I'm not in linux now, I just saw it in a tread and thought that it could be a solution, but you need to check whether you find something inside it (don't even now whether it's a file or a folder).

---

### Post by barryp3uk on 2006-03-24
Ye-es

Gedit seemed a reasonable way of looking inside something if it was a file. Turns out it probably wasn't. What was it? I don't know - I did a search for it which didn't turn up anything.

I see these little things as opportunities to learn but I'm not sure what it is I'm actually supposed to be learning.

Cheers!

Barry.

---

