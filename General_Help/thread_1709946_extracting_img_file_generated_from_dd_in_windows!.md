---
title: "extracting img file generated from dd in windows?!"
date: 2011-03-19
forum: General Help
---

### Post by Bannaz on 2011-03-19
Hi,
I have a bit of situation here...
I run ubuntu and xp on my machine

then my ubuntu drive was unmountable so I tried checking the file system from a live cd of 10.10 and failed and then I found a solution...

its to copy the whole drive into a big fat image file and then check it n finally copy it back/extract the img file using these commands
[B]
sudo mkdir /mnt/b[FONT=monospace]
[/FONT]sudo mount /dev/sda4 /mnt/b
sudo dd if=/dev/sda1 of=/mnt/b/sda1.img
sudo e2fsck -y /mnt/b/sda1.img[/B]

and it went fine but it wouldn't be copied back to the drive using[SIZE=3]
[B][SIZE=1][COLOR=black]
sudo dd if=/mnt/b/sda1.img of=/dev/sda1[/COLOR][/SIZE][/B][/SIZE] 

so I mounted the img file into a loop and thought I could copy it manually with root privileges in nautilus using

[B]sudo mkdir /mnt/loopa
sudo mount -o loop /mnt/b/sda1.img /mnt/loopa[/B]

but of course it didn't work becuase I couldn't copy the special files! (duuuh!)

so another plan was to copy them from windows which won't recognize that the files are special but I couldn't get the img file to work on windows!

so is there a way to extract or emulate that img file resulting from the disk copy using dd in windows? (NOT MagicIso! it doesn't work!!)

just one last thing.....I changed the ext4 ubuntu drive to NTFS temporarialy in order to get windows to read it
Also...the file is 10GB and MagicIso said its too large to mount...
sorry for being alittle talky
okay go... 
think think think:D

---

