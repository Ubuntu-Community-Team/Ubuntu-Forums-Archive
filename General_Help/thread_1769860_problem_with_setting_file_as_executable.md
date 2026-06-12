---
title: "problem with setting file as executable"
date: 2011-05-28
forum: General Help
---

### Post by blastbeast on 2011-05-28
I have a file in my system. Its named lastPod.sh. I'm trying to run it but when i double click on it i get the message "The file '/media/New Volume/000 OLD UBUNTU DESKTOP/lastPod/lastPod.sh' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.". To fix this when i right click on the file and goto properties>permissions and check the box labelled "allow executing file as program" its getting unchecked by itself the next moment. I also tried running the command "gksu nautilus /media/"New Volume"/"000 OLD UBUNTU DESKTOP"/lastPod" on the terminal and then changing the permissions on the file but didnt work work. Still the same checkbox getting unmarked. Does anyone know how to fix this? I'm running Ubuntu 10.10. Any help would be much appreciated.:)

---

### Post by ram0042 on 2011-05-28
> **blastbeast said:**
> I have a file in my system. Its named lastPod.sh. I'm trying to run it but when i double click on it i get the message "The file '/media/New Volume/000 OLD UBUNTU DESKTOP/lastPod/lastPod.sh' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.". To fix this when i right click on the file and goto properties>permissions and check the box labelled "allow executing file as program" its getting unchecked by itself the next moment. I also tried running the command "gksu nautilus /media/"New Volume"/"000 OLD UBUNTU DESKTOP"/lastPod" on the terminal and then changing the permissions on the file but didnt work work. Still the same checkbox getting unmarked. Does anyone know how to fix this? I'm running Ubuntu 10.10. Any help would be much appreciated.:)
It can only be marked excecutable when it is inside your /home

---

### Post by prodigy_ on 2011-05-28
Don't use Nautilus for that (AFAIK it never worked properly), use command line:```
chmod +x /<path>/<to>/<file-name>
``` (if you get "Operation not permitted" error message, you don't have write permission for the file and need to use **sudo**).

---

### Post by mc4man on 2011-05-28
well you could put the script on a volume where you can set permissions or mount the device without the showexe option or rebuild udisks and edit the default mount options

It is possible however  to 'fool' udisks if your volume is vfat(16 or 32
By default all .exe files will have the execute bit set when mounting

The way to fool is copy any scripts to your install (Desktop. whatever
Then rename them by  adding .exe to name and copy back to the volume in question.
You can then execute them by d. clicking on ( even if wine is installed won't matter, they will be run.

The trick is you can't rename them on the volume - you must copy out and then paste back - screen shows - all are shell scripts - the 2 with icons where copied and pasted back, the one in middle was just renamed on the volume
The 2 with icons can be run directly from the volume (FAT32

---

### Post by ram0042 on 2011-05-28
> **mc4man said:**
> well you could put the script on a volume where you can set permissions or mount the device without the showexe option or rebuild udisks and edit the default mount options

It is possible however  to 'fool' udisks if your volume is vfat(16 or 32
By default all .exe files will have the execute bit set when mounting

The way to fool is copy any scripts to your install (Desktop. whatever
Then rename them by  adding .exe to name and copy back to the volume in question.
You can then execute them by d. clicking on ( even if wine is installed won't matter, they will be run.

The trick is you can't rename them on the volume - you must copy out and then paste back - screen shows - all are shell scripts - the 2 with icons where copied and pasted back, the one in middle was just renamed on the volume
The 2 with icons can be run directly from the volume (FAT32
Wow, I did not know that. Too, complicated, in my opinion, but I could find some use for that in more permanent situations.

---

### Post by monko909 on 2011-06-18
If you install NTFS-Config and give yourself read/write permissions, that should do it.

---

### Post by greasegum on 2011-07-02
> **ram0042 said:**
> It can only be marked excecutable when it is inside your /home
Wow, I've been scratching my head over this for days. Finally something that kinda works. However, if I take that executable from my /home and put it on say a USB drive, it will revert back to non-executable. This seems really strange to me. Any advice on how to make these files retain their executable bit?

Thanks!

---

### Post by RoyLongbottom on 2011-07-02
> **greasegum said:**
> Wow, I've been scratching my head over this for days. Finally something that kinda works. However, if I take that executable from my /home and put it on say a USB drive, it will revert back to non-executable. This seems really strange to me. Any advice on how to make these files retain their executable bit?
 
Thanks!
 
Use Disk Manager to create such as an Ext4 partition on the USB drive. 
 
I also use a script file to open Terminal to see the program running. Create Document, Empty file, rename as runit, enter file name like ./test, Save, select Properties, Permissions, tick Allow Execution. Clicking on this provides options to Run In Terminal or Display.
 
Roy

---

