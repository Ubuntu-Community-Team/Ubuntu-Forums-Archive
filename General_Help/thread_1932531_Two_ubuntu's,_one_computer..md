---
title: "Two ubuntu's, one computer."
date: 2012-02-27
forum: General Help
---

### Post by kroeze on 2012-02-27
I have installed Ubuntu twice on my computer and am looking to uninstall one of them.

---

### Post by MARP1961 on 2012-02-27
Boot up your computer with an Ubuntu CD and then select the 'Try Ubuntu' option. Open the application 'Gparted'. This partition editor can then be used to delete the partitions you don't want. Make sure you back up any data you want to keep first.

Of course, the simplest way to have one Ubuntu would be to do a fresh install and instruct Ubuntu to install using the whole hard drive.

---

### Post by Scott Baker on 2012-02-27
If you haven't got a lot, or nothing to backup, you might as well start fresh. It will save you some headaches in the long run. Good luck.

---

### Post by forrestcupp on 2012-02-27
If you delete an Ubuntu partition, you may need to restore Grub, too, if it doesn't work. Make sure you back up your files before you go deleting partitions, though.

---

### Post by Paqman on 2012-02-27
Once you've deleted the other system and booted up into the main one run:
```
sudo update-grub
```
This will get Grub to rebuild it's list of available systems and you won't get the other one showing up at boot any more.

---

### Post by idoitprone on 2012-02-28
boot the partition you want to keep

run these commands
> sudo grub-install /dev/sda

sudo update-grubthis will ensure you dont delete the partion that has the bootloader in the mbr.

---

### Post by kroeze on 2012-03-01
Thanks guys! It's all fixed now! :D

Not sure how to mark as solved though.

---

