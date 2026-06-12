---
title: "not able to write image to Flash drive to install ubuntu netbook remix"
date: 2009-09-04
forum: General Help
---

### Post by ryansdistrict on 2009-09-04
hello i was trying to install ubuntu remix on my netbook Toshiba NB100 
i downloaded the .IMG file which is like 900mb from ubuntu website and am supposed to write the image of it on the 1gb flash drive i got so that i boot via usb and install it 
i tried the Win32 Disk Imager software which was recommended in the ubuntu tutorial but no luck
i dont know why nothing is written on the flash drive 
i tried 2 flash drives i got and both i was not able to write to 
btw i am trying to create the bootable flash drive fro mmy windows XP not from linux
Please can u help me fixing this issue

---

### Post by nothingspecial on 2009-09-04
Try [[COLOR="Magenta"]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by ryansdistrict on 2009-09-04
i tried this too no luck

---

### Post by ryansdistrict on 2009-09-04
oh it worked after choosing the floppy thing thx :)

---

### Post by P4man on 2009-09-04
you're not the first one to report this.. I wonder whats up with that?
Can you verify your download is good?

A few other things you might want to try: delete the partition from the USB stick before to put the image on it.

Rename the .img to .iso and burn it to a DVD with some program that can burn iso's (reportedly this works, but I havent tried it). Boot from the DVD.

If you're desperate: boot from a normal ubuntu live CD, then make the netbook remix stick from there with the USB creator.

edit: too late heh.

---

### Post by ryansdistrict on 2009-09-04
hey p4man i finaly was able to fix this issue and now its working perfectly 
for .img files in this program  u must select in disk image section >> select floppy instead of iso in the drop list and choose the .img file 

i think it worked perfectly 
but when i booted form it my pc it did boot but after sometime in loading files i faced another issue where an error shot " No active partition..."
Please can u help me in this issue too [http://ubuntuforums.org/showthread.php?p=7895497#post7895497](http://ubuntuforums.org/showthread.php?p=7895497#post7895497) 
thanks

---

