---
title: "How to toggle a script"
date: 2006-05-29
forum: General Help
---

### Post by Fred Doolie on 2006-05-29
I have a script that says:
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

and one that says:
sudo umount /dev/hda1

These work great for mounting and unmounting my Winblows partition.

Is there a way to combine them into one script like this?
-------------------------------------------------
IF HDA1 is mounted then
sudo umount /dev/hda1
else
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
-----------------------------------------------
Thanks

---

### Post by simonn on 2006-05-29
```

if [ -z "`mount | grep "/dev/hda1 "`" ]; then
  sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
else
  sudo umount /dev/hda1
fi

```

The space after /dev/hda1 is important, e.g. /dev/hda10 would match if there was not a space.

---

### Post by Fred Doolie on 2006-06-06
Hot dog! Thank you!

Using this for a template I'll make one for my external drive(s) too.

I love the fact that Linux can mount and unmount devices as you wish for safety. Stupid Winblows can't do that!

---

