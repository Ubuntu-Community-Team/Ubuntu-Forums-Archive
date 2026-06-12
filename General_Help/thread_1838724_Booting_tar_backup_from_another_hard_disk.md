---
title: "Booting tar backup from another hard disk"
date: 2011-09-04
forum: General Help
---

### Post by mcemsi on 2011-09-04
Hi,

I used to create backups using tar on the root directory /
Now my HDD broke down, and i bought another one, created a bootable ext3 partition and extracted the backup on it.

Unfortunately there seems to be some more linux magic necessary to make that work.

I only see a blinking _ when trying to boot from it.


I reinstalled grub on the partition and was able to get to the grub prompt.
The command 
**configfile (hd0,1)/boot/grub/grub.cfg**
tells me that there is s.th wrong with the config file.

(For sure, because the whole device ID stuff doesn't match the new devices ID ect)


I hope you understand my problem :) TIA

---

### Post by Lampi on 2011-09-04
It's most likely caused by different UUID of your new root partition. The easiest way should be changing it back to the same it was, otherwise you will have to edit more files

get the previous uuid of your old drive from grub.cfg, then change the uuid of the new drive like this:

```
tune2fs -U <UUID> /dev/yournewrootpartition
```

that might be all

---

### Post by mcemsi on 2011-09-04
Thanks for your reply,
i used tune2fs, but i'm still getting to the grub prompt.

Now i was able to use the configfile command on the grub.cfg but without any effect (no error, no success). 

I tried loading the kernel using

linux /vmlinuz root=/dev/sda2 ro

but it tells me that the file could not be found.
My backup includes the vmlinuz file but it is 0 bytes of size.

(It seems to be a link to boot/vmlinuz-2.6.38-10-generic-pae or s.th like that?! but this file also doesnt exist in my backup)


****

---

### Post by Lampi on 2011-09-04
What other vmlinuz files you got in /boot ?

Remember you can use tab expansion in the grub config menu to list files in a folder

Also don't forget to load initrd

If you miss vmlinuz you can download the linux-image debian package and just extract this file, but I wonder what else is messed up in your backup if vmlinuz is missing?

---

