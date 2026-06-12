---
title: "kicked out of sudoers list"
date: 2006-04-09
forum: General Help
---

### Post by Second_Player on 2006-04-09
i deleted a second administrative account that i made but didnt do anything with and after that it says i cant do anything basically because i'm not on the sudoers list, i have no clue what i did wrong because my normal account should still be the administraive one but now its not.  if somone could please help me get back on that list that would be great, i dont want to have to reinstall again.
thankyou

---

### Post by Celerex on 2006-04-09
You might need to reboot into single user mode (the 'Recovery' option in your gurb/lilo list) to get at this. Failing that use an install cd and mount your hd on a directory somewhere.

Basically check /etc/sudoers for your username. For my config I have:
<user> ALL=(ALL) ALL and I can pretty much do everything.

---

### Post by nanotube on 2006-04-09
reboot into "recovery mode", and from there edit your /etc/group to make sure your user is still in the "admin" and/or "adm" group. 
if it is, then try "visudo" and see if the admin group is allowed to sudo, and if not, add that.

---

### Post by Second_Player on 2006-04-09
i'm using a mac/ppc, i dont have a grub loader, sorry for not putting that in my post

---

### Post by nanotube on 2006-04-09
in that case, boot from a live cd.

---

### Post by Second_Player on 2006-04-10
i'll try, i'm not sure that it will work, i dont remember the live cd working, i'll give it a try though
thanks

---

### Post by Second_Player on 2006-04-10
nope, i guess if i knew how to edit documents from the command line then i could, but i dont get the gtk, so what should i try now.

---

### Post by aysiu on 2006-04-10
[QUOTE=Second_Player]nope, i guess if i knew how to edit documents from the command line then i could, but i dont get the gtk, so what should i try now.[/QUOTE] ```
sudo cp /directory/name_of_file /directory/name_of_file_backup
sudo nano /directory/name_of_file
``` When you're done, save (control-x), confirm (y), exit (Enter).

---

### Post by Second_Player on 2006-04-10
do i need to mount or switch to the harddrive somehow
i want to be completely sure how to do everything before i try again

---

### Post by aysiu on 2006-04-10
[QUOTE=Second_Player]do i need to mount or switch to the harddrive somehow
i want to be completely sure how to do everything before i try again[/QUOTE] Would you be using recovery mode or a live CD?

---

### Post by Second_Player on 2006-04-10
live cd, i dont have the  grub loader, i'm using a mac

---

### Post by aysiu on 2006-04-10
Okay. I'm not well-versed in Mac, but I think this is what you do.

Put in the live CD. Hold down the **c** key while booting up.

Open a terminal and type ```
sudo fdisk -l
``` Figure out which is your Ubuntu partition--let's just say it's /dev/hda1 and HFS+ ```
sudo mkdir /recovery
sudo mount -t hfsplus /dev/hda1 /recovery
gksudo nautilus
``` Go to /recovery/etc/group and add yourself to admin.

---

### Post by Second_Player on 2006-04-10
is the hfs+ the name of the partition, i dont know why you put it there.

---

### Post by aysiu on 2006-04-10
[QUOTE=Second_Player]is the hfs+ the name of the partition, i dont know why you put it there.[/QUOTE] hfs+ is probably the filesystem the partition uses. The syntax goes: ```
sudo mount -t *filesystem-type* *partition-location* *mount-point*
```

So, to translate the original instructions:

**sudo**: with root privileges
**mount**: mount
**-t**: the partition of type
**hfsplus**: hfs+ filesystem
**/dev/hda1**: that lives at hda1
**/recovery**: to the mount point /recovery

---

### Post by Second_Player on 2006-04-10
you read that i dont have a gtk right, nothing but black and white for some reason on the live cd

---

### Post by Second_Player on 2006-04-11
i'm just reinstalling, seems like it might be easier, sure dont want to though

---

