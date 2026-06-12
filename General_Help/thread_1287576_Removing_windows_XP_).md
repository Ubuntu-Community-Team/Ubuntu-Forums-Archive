---
title: "Removing windows XP :)"
date: 2009-10-10
forum: General Help
---

### Post by baskar007 on 2009-10-10
hi friends,
after a long thinking i have decided to Remove windows from my PC and keeping ubuntu as a only OS!

friends i need your advice.

currently i have dual boot of Ubuntu and XP. If i remove XP, ubuntu got any problem like booting or working?

---

### Post by MelDJ on 2009-10-10
try going through this: [http://ubuntuforums.org/showthread.php?t=1029758](http://ubuntuforums.org/showthread.php?t=1029758)

---

### Post by baskar007 on 2009-10-10
Now i have no windows.
THank you/

---

### Post by GolemdX on 2009-10-10
If they're on separate partitions, go into Gnome Partition Editor in System > Administration. If you don't have it...

```
sudo apt-get install gparted
```

...and then run it. Choose the hard drive it's on in the top right corner, select the partition, and BLAST IT (delete it)! It should be the only partition with the type of NTFS, if not, it should say the size and just go by that. Feel free to select your ubuntu partition and resize it to fill up that empty space now.

If you're unsure, post a screenshot (taken using Print Screen).

If Windows is still appearing in grub, when you boot, run...

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```
(to backup it)

then

```
sudo gedit /boot/grub/menu.lst
```

and remove that block of text that looks like this:

```
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
```

Just delete the whole thing, but nothing from the other entries!
Save... and then it should be gone. There might be a line of text that says 'Other Operating Systems' or something similar, feel free to remove that as you won't be needing it anymore.

EDIT: The time it took me to write this... you're already done :). Oh well.

---

