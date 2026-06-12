---
title: "mount /bin to ramdisk"
date: 2009-09-17
forum: General Help
---

### Post by hwttdz on 2009-09-17
Warning: read [this]("http://ubuntuforums.org/showthread.php?p=7964590#post7964590") first

Would it improve system performance some if one were to mount /bin to a ramdisk?  How could one go about doing this?  Of course assuming sufficient system memory.

---

### Post by Bachstelze on 2009-09-17
> **hwttdz said:**
> Would it improve system performance some if one were to mount /bin to a ramdisk?  How could one go about doing this?  Of course assuming sufficient system memory.

I doubt you would see any difference in performance.

---

### Post by schmidtbag on 2009-09-17
it still has to be loaded elsewhere so no, it won't make a difference.  if you were to do something like the /proc folder which is all temporary files, you may see a performance difference.

---

### Post by hwttdz on 2009-09-17
By "it has to be loaded elsewhere" you mean it's impossible to point to the ramdisk instead of /bin on a hard disk?

---

### Post by winotree on 2009-09-17
On my small device I've found a simple solution that works just enough (in my mind) to be noticeable: add this new string to **about:config** ```
browser.cache.disk.parent_directory
``` and mark the new string as ```
/tmp
``` This moves Firefox's cache to /tmp -- in effect speeding your browser *but* *not saving anything* on shut-down.  It took me awhile to notice the effects -- why not see what it does for you.  ;)

---

### Post by schmidtbag on 2009-09-17
> **hwttdz said:**
> By "it has to be loaded elsewhere" you mean it's impossible to point to the ramdisk instead of /bin on a hard disk?

yes, because ramdisks are temporary, so all information would be lost.  you CAN write a script to copy all of the /bin files from a source to a ramdisk, but when you type them in terminal, it'll still load it from the source drive

---

### Post by hwttdz on 2009-09-17
Ok, I follow that.  Couldn't one copy to a ramdisk after start up then unmount /bin and mount the ramdisk as /bin (I realize there is no performance benefit from this, now I'm just learning about the theory).

---

### Post by scorp123 on 2009-09-17
Oh dear ... Before anyone hoses their system, let's do a reality check, yes?

**/bin**, **/sbin**, **/lib** and **/etc** [COLOR="Red"]**__CANNOT__**[/COLOR] be on separate file systems. Amen. End of story.

These locations [COLOR="Red"]**__ABSOLUTELY__**[/COLOR] _**[COLOR="Red"]must[/COLOR]**_ remain on **/**

What you can do, though:
[LIST]
[*]Have /boot separated from the rest on a small partition
[*]Boot via PXE, TFTP etc. and then mount "/" via NFS (thin-client nodes work like that)
[*]You can have /usr on a separate large partition (5 GB or more recommended)
[*]/usr could also reside on an NFS mount (when disk space was rare and hard disks very expensive many computers were setup like this: they would mount /usr and /opt from remote locations and only have a few essential directories locally ...)
[*](BTW: /usr/local comes from that age: it was meant to inform the user that those applications there indeed were local on their machine and not remotely mounted like the rest of /usr ....)
[/LIST]

So ... **[COLOR="Red"]DO NOT[/COLOR]** move **/bin**, **/sbin**, **/etc** and **/lib** to any other partitions! Especially not RAM disks. [COLOR="Red"]**You will hose your system.**[/COLOR]

[COLOR="SeaGreen"]**/usr**[/COLOR], [COLOR="SeaGreen"]**/opt**[/COLOR], **[COLOR="SeaGreen"]/tmp[/COLOR]** and **[COLOR="SeaGreen"]/var[/COLOR]** _can_ be moved ... but don't forget to edit your **/etc/fstab** if you do that.

---

