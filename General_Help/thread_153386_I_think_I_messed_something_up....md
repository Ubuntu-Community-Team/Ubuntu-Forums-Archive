---
title: "I think I messed something up..."
date: 2006-03-31
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-03-31
I installed the 2.6.14 kernel. I set it up and all that stuff. Now where I restarted, I get Grub error 22. What should I do ? Re-install ?

---

### Post by xXx 0wn3d xXx on 2006-03-31
does anyone know how I can fix this ?

---

### Post by frup on 2006-03-31
i would suggest using a live CD of some sort to try and edit grubs menu.lst looks like somethings pointing to the wrong place

grub error 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

---

### Post by xXx 0wn3d xXx on 2006-03-31
[QUOTE=frup]i would suggest using a live CD of some sort to try and edit grubs menu.lst looks like somethings pointing to the wrong place

grub error 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.[/QUOTE]
Thanks but I'll just reinstall. I didn't really have anything valueable except my wifi settings and bookmarks, it wouldn't be worth it to download and burn the live cd when I have a cd.

---

### Post by krusbjorn on 2006-03-31
If you get into the grub menu, you can temporarily edit the boot entry by pressing 'e' while selected. That way, you can boot into Ubuntu and edit the file to make it work properly.

---

### Post by chettyk on 2006-04-01
[QUOTE=MasterChief1234]Thanks but I'll just reinstall. I didn't really have anything valueable except my wifi settings and bookmarks, it wouldn't be worth it to download and burn the live cd when I have a cd.[/QUOTE]

Even if you reinstall, when you update, you will run into the same problem again. Besides, it is not difficult to fix. It happened to me just this morning when my kernel was updated.

When the Grub menu comes up, choose the system you want to boot and then press the letter 'e". That will let you edit the the Grub entries for that system. The first entry will be something like:

root (hd1,0)

Make sure that line is highlighted and again press the letter 'e'

In my case, the only change I had to make was change (hd1,0) to (hd0,0). If, however, you have Windows XP (or some other operating system in the first partition) and Ubuntu is on the second partition, your entry may need to be (hd0,1). 

Once you have made the requisite changes to the line, press <enter> to set the changes and then the letter 'b' to boot the system.

If this works correctly, then you need to make the changes permanent by modifying Grub's menu.lst. First open a terminal window (Applications > Accessories > Terminal). Type (or cut-and-paste) the following:

```
sudo gedit /boot/grub/menu.lst
```

Scroll down to the first entry after the line **## ## End Default Options ##**. Make the necessary changes in the line starting with 'root'.

It would be as well to make the same changes in the next set of entries; the title for this set will have "(recovery mode)" at the end of the title line.

Hope this works.

---

