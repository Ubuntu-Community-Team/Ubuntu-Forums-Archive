---
title: "Is it possible to change filesystems?"
date: 2011-03-18
forum: General Help
---

### Post by umwhat on 2011-03-18
please, bear with me here, because I don't know what I'm talking about or how to explain it:

*ubuntu1 is my first and oldest ubuntu
*ubuntu2 is my most recent one from about a month ago

1. I restarted this laptop and I had some grub rescue error.

2. I booted up from the ubuntu demo disc and i was able to reinstall grub through the terminal.

3. I had reinstalled ubuntu before, so I had 2(4 because of the "recovery mode" options)ubuntu things, but only ubuntu2 worked after the re-installation.

4. after installing the grub stuff again, only ubuntu1 was available, which works now for whatever reason, and ubuntu2 is gone.

5. I have almost no free space left on ubuntu1, but the ubuntu2 filesystem is still there in the filebrowser sidebar. i tried copying the folders from ubuntu2 into ubuntu1 so i could get my data back, but I don't have enough space in ubuntu1.

is there any way i could somehow get these things back into ubuntu1? or maybe i could boot from ubuntu2's filesystem? i tried using Disk Usage Manager, but nothing taking up much space was found. :(

---

### Post by Alex1357 on 2011-03-18
You could use parted or the graphical front-end gparted to change the sizes of the partitions. But remember that 
1. you cannot change the partitions you currently use so you have to boot e.g. from the Ubuntu CD. 
2. you make a backup to an external disk before you change the partitions because those operations are considered risky.
3. That can take long time.

---

### Post by coldraven on 2011-03-18
First think about backing up you data.
Buy an external USB drive, they are not expensive for a 250GB model.
Plug it in and boot up with a live CD.
If you do not have large files over 4GB (movies for example) then just copy all your files onto the external drive.
If you do have files over 4GB then you will most likely need to format the external drive from FAT32 to NTFS. NTFS is useful because Windows PCs can read/write to it as well as Ubuntu.
You can run Gparted from the live CD to format it, just make sure that you select the correct drive from the drop-down menu in the top right corner.
I'm lazy and I have a 1TB USB drive so I just copy the whole /home folder to a folder called Backup-9.04 for example.
The the next time I would copy the /home folder to Backup-10.04.
Anyway, once you have copied your files you can consider your options.
Personally I would blank the hard disc and go for a fresh install of the latest Ubuntu which is 10.10 (maverick meerkat).
Or you could delete the older install and use that space. Your choice :p

---

