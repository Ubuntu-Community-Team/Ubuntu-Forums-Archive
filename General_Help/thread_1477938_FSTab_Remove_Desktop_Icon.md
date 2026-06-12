---
title: "FSTab Remove Desktop Icon?"
date: 2010-05-09
forum: General Help
---

### Post by Penguin Guy on 2010-05-09
I have a 'Home' partition which I store all my personal stuff in, I have an entry in [FONT="Courier New"]/etc/fsatb[/FONT] that mounts it at [FONT="Courier New"]/home/josh/Home[/FONT]. However Nautilus also puts an icon on my desktop - how do I get rid of this icon?
```

[COLOR="Red"]UUID=76ee7299-a906-4429-8192-e983685c0452  **/home/josh/Home**  ext4 noatime  0  2[/COLOR]

```
Solution: Make sure it isn't mounted in [FONT="Courier New"]/media[/FONT] or [FONT="Courier New"]/home[/FONT]:
```

[COLOR="Green"]UUID=76ee7299-a906-4429-8192-e983685c0452  **/mnt/Home**  ext4 noatime  0  2[/COLOR]

```

Thanks everyone for the help.

Related threads:
[LIST]
[*][fstab automount entry, no desktop icon option ?]("http://ubuntuforums.org/showthread.php?t=1162223")
[*][Hide Partitions/Drives from Nautilus (side panel)]("http://ubuntuforums.org/showthread.php?t=1496408")
[/LIST]

---

### Post by Penguin Guy on 2010-05-16
Still no ideas?

---

### Post by ixifx on 2010-05-29
try running 

gconf-editor

and from there going to 

apps\nautilus\desktop\

there are options there for what will show up on the desktop.  do be careful, though, as this is pretty much the equivalent of regedit in windows (VERY BREAKABLE).

hope this helps =)

---

### Post by Penguin Guy on 2010-05-29
[@ixifx]("http://ubuntuforums.org/showthread.php?p=9378422#post9378422")

> **Penguin Guy said:**
> I only want to get rid of this specific icon, I still want other drives to appear on my desktop.
The [FONT="Courier New"]/apps/nautilus/desktop/volumes_visible[/FONT] option affects all volumes.

---

### Post by Wicca on 2010-05-29
In the same pane you'll find home_icon_visible. Uncheck that. (/apps/nautilus/desktop/home_icon_visible)

---

### Post by John Bean on 2010-05-29
> **Penguin Guy said:**
> I only want to get rid of this specific icon, I still want other drives to appear on my desktop

Mount it somewhere other than your home directory - /mnt is a good place - then it will be ignored by nautilus and not appear on the desktop. Replace your existing ~/Home mountpoint folder with a symlink (of the same name) to /mnt/Home (or wherever) and it will all work just as it did before... but without the desktop icon.

---

### Post by Morbius1 on 2010-05-29
Anything mounted to your /home/josh or /media directory will show up on the desktop by default. Anything mounted in /mnt or "/" itself will not.

You could change the mount point to say ... /mnt/Home but then you have some cleanup to do:

(1) Take possession of the mountpoint:
```
sudo chown -R josh /mnt/Home
```(2) When you open Nautilus manuvering to /mnt/Home is a little awkward and not as easy as having it under your home folder so "Bookmark" it:

In Nautilus, go to /mnt/Home then select "Bookmarks" > "Add Bookmark".
It will then show up under "Places"

---

### Post by Morbius1 on 2010-05-29
John Bean, Sorry - similar ideas - sorry for the intrusion.

---

### Post by John Bean on 2010-05-29
> **Morbius1 said:**
> John Bean, Sorry - similar ideas - sorry for the intrusion.

Hey, no apology needed. You added valuable extra advice about ownership issues that I took for granted but may have tripped up some people.

---

### Post by Penguin Guy on 2010-05-29
> **Wicca said:**
> In the same pane you'll find home_icon_visible. Uncheck that. (/apps/nautilus/desktop/home_icon_visible)
Since it's not my actual home directory (just a directory called 'Home'), this won't work.


Thanks to John Bean and Morbius1 everything is now working fine - thanks everyone for the help!

---

