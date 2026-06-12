---
title: "need to fix grub"
date: 2006-04-22
forum: General Help
---

### Post by oldmanstan on 2006-04-22
ok, dapper beta apparently broke my grub, i installed it and my computer refused to boot using the HD, i kept getting grub error 15, which as far as i can tell is a file not found error but i have no clue which file is not being found

my setup is such that dapper was installed on hda and breezy on hdc (hda used to be windows, i dual booted for awhile then i got rid of windows and started using hda to install testing versions of ubuntu just to play around with them)

so since there was an error i thought maybe i could boot straight off of hdc so i set the bios to boot off the second hard drive, this yielded a cannot start OS error

dapper backed up my old .lst file for grub so i tried going back to that one (grub is installed on hdc) but it didn't change anything

any ideas? my files and whatnot are all still intact (i'm using the dapper live cd right now) but i just can't boot from the hard drive

thanks!

---

### Post by z_diver on 2006-04-22
If you can get to the grub list, which it sounds like you can, press "c" to get to the grub prompt.  At the grub prompt, type
```
grub> [COLOR="Navy"]find /boot/grub/stage1[/COLOR]
```
That will give you a list of partitions grub can find installations on. Choose your original Ubuntu partition and run the command below replacing the variables as necessary. NOTE: root (hd2,1) would mean /boot/grub/menu.lst is to be found on /dev/hdc partition 2.  And grub can read drives differently than ubuntu hence the reason for the find command above
```
grub> [COLOR="Navy"]root (hdx,y)[/COLOR]
Filesystem type is ext2fs, partition type 0x83
grub> [COLOR="Navy"]setup (hdx)[/COLOR]
grub> [COLOR="Navy"]quit[/COLOR]
```
If the output shows "succeeded" you should be able to boot from your old ubuntu installation but that will also mean that you have to make sure it's menu.lst accurately represents the partition structure.

---

### Post by oldmanstan on 2006-04-22
only problem is that it never gets to the grub list, it errors out before it gets there

---

### Post by Dr Gonzo on 2006-04-22
It'd be best if you could reinstall grub, probably.

You should find a livecd with grub on it.  I'm not sure if the Ubuntu liveCD does, but it might.  I'm pretty sure that Gentoo liveCDs have it, especially the universal one.  Alternatively, you can make a grub boot floppy and use that.

From a command line on the liveCD, type "grub".  You'll get the grub command prompt.  Now, you said that the installation you want is on hda.  I'm going to assume that / is on /dev/hda1.So, do this:```
root (hd0,0)
setup (hd0)
```  Make sure that, after the root command, it tells you that it found the right filesystem and all that.

You should now be able to reboot off of hda.

---

### Post by oldmanstan on 2006-04-22
i get this error

```
Error 21: Selected disk does not exist
```

when i do root(hd0,0) and also when i change it around with different values that should also work (using hdc)

---

### Post by oldmanstan on 2006-04-23
ok, problem solved

basically what i ended up doing is reinstalling dapper which apparently installed correctly the second time around. originally it didn't put grub on hda where it was installed and tried to use the copy that was already on hdc. this time it installed its own copy of grub on hda. so i just edited the menu.lst file on hda to include breezy on hdc and now i can boot both.

it's sort of a messy solution but it will work for now, after dapper gets released im gonna redo the whole setup anyway

thanks to everyone who helped!

---

### Post by sinkxdie on 2006-04-23
Congrats to getting it to work.
:D

---

