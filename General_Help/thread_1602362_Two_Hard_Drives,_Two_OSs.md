---
title: "Two Hard Drives, Two OSs"
date: 2010-10-21
forum: General Help
---

### Post by CrusaderAD on 2010-10-21
I dropped 10.10 on my new machine. Fresh equipment and everything, feels goods. I need to drop another slave hard drive on there with windows for work. I know I can install on separate drives, but will I be able to dual boot when I fire both up?

---

### Post by 3Miro on 2010-10-21
You mean a separate hard-drive, right?

If you already have Ubuntu, then it is probably best to first disconnect the Ubuntu drive, install windows and then reconnect the Ubuntu drive. That way windows will not overwrite the Ubuntu MBR and you will be able to boot into Linux just fine. Once in Ubuntu, you can run:
```
 sudo update-grub 
```
to add the windows entry to the Ubuntu Grub startup menu.

On another note, on some motherboards, you can explicitly specify the harddrive that you want to boot form. I don't have Windows entry on my Grub, to go to windows, I simply hit F12 on boot, then select HDD and pick the HDD with windows (other wise it automatically goes into Linux).

---

### Post by CrusaderAD on 2010-10-21
Awesome I'll give that a shot. It's a new system so it might have the boot option at start up. Sounds simple enough. Thanks!

---

