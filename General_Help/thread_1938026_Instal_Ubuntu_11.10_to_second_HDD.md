---
title: "Instal Ubuntu 11.10 to second HDD"
date: 2012-03-08
forum: General Help
---

### Post by Serilicius on 2012-03-08
I was wondering if you can migrate wubi and install it to a second hard drive. Thanks in advance.

---

### Post by Jon Monreal on 2012-03-08
Yes, you should be able to migrate wubi to a second hard drive as long as it is already partitioned (as outlined [here]("https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F")), with the caveat that grub will replace your bootloader and there's always a chance things won't work as expected.

If you need help partitioning the drive (using your Ubuntu installation in wubi), please feel free to ask.

---

### Post by Serilicius on 2012-03-09
Ok, so I have a Msi GT-780 With 2 500 GB Hard Drives. I don't want to get rid of windows, I want to dual boot ubuntu and windows and have them in separate hard drives. And I don't really know how.

---

### Post by Jon Monreal on 2012-03-09
I'm supposing here that the external hard drive contains no files or anything important; if it does, you should move them to your Windows installation before continuing.

Okay, you're going to need to boot into your wubi installation, open a terminal, and type "apt-get install gparted" (minus the quotes) to install the gnome partition editor. After it installs, start typing gparted in the unity menu and open gparted. When it comes up, you'll want to go to the upper right of the window where it likely says "/dev/sda" and switch it to the other option with a large amount of space, which should be the second hard drive. Make sure that the size a significant chunk of the drive isn't used under the used columns (which would indicate that there are files on the drive, or that you've selected your Windows drive). If not, then right-click on the partition in the menu "likely /dev/sdb1" and click 
"Unmount." After this, right-click, and click, "Delete." Next, right-click where it says "unallocated" and select "New." Change the "File system" part to "linux-swap" and set the "New size (MiB) parameter to an amount equal or greater to your amount of RAM in MiB (or 1024 for every 1 GB of RAM that you have). Click "Add." Then, right-click again on the unallocated space and select "New." Under "File system" select ext4, and click "Add." When you're finished, you can click the green check above to execute the pending operations and format your drive. When the operations are completed, check and see what the partition names are for the ext4 and the swap (such as /dev/sdb1, /dev/sdb2) and write them down in that order.

From there, you can follow [these instructions]("http://ubuntuforums.org/showthread.php?t=1519354"), under the section to migrate automatically, using the second set with swap, and replacing the red text with your ext4 partition name and the blue text with your swap partition name.

If you need additional assistance with any step of this process, please feel free to ask.

---

### Post by Serilicius on 2012-03-09
I'll try it today. Thank you

---

### Post by Serilicius on 2012-03-10
I managed to install ubuntu but now i cant se the unity dash. If I login as a guest i can use the unity dash but in my user I cant. All i see is where -file edit view go bookmarks and help- are. Any ideas what is happening?

---

### Post by Serilicius on 2012-03-10
I found this and it solved my problems :D
unity --reset

---

