---
title: "cannot display this video mode"
date: 2011-10-09
forum: General Help
---

### Post by twynn401 on 2011-10-09
I ran update (ubuntu 11.4) it asked me to retart. When I did I now get this message at startup and cannot find a way to get into the system at all.  I am not dual booting tjhis is the only operating system on the machine
Help please I have a lot of info on here that I do not want to lose

---

### Post by searchfgold6789 on 2011-10-09
EDIT: What is the exact error you get, and what hardware do you have?

---

### Post by twynn401 on 2011-10-09
I have a dell optiplex 270 and a dell flatscreen monitor (I could not find the model # on it)  I am using the onboard video - it has worked fine for several months now untill I did this latest update.  the exact message is "Cannot display this video mode  optimum resolution 1280 X 1024 60 Hz"

---

### Post by searchfgold6789 on 2011-10-09
OK, at what point does the system freeze? right after the Dell splash screen? is there an Ubuntu scrollbar first?
If you can, try seeing if there is a resolution selection or other options in the BIOS or setup program.

---

### Post by twynn401 on 2011-10-09
I see the dell splash screen the the screen blanks and the cursor flashes in the upper right hand corner for a brief time then I get a black screen and the error message.  I have tried everything I know to get to a text cursor or anything other than the error screen but no luck.

---

### Post by searchfgold6789 on 2011-10-10
OK, you can try reinstalling Grub since I have received a similar message before and it was fixed when I reinstalled Grub. There are instructions on how to do that [Here]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2").

---

### Post by drs305 on 2011-10-10
I was experimenting with some boot issues yesterday and ran into some video problems with Lubuntu. I did not get the error message that you did, but I do know that there have been issues with Grub not identifying and passing along the proper resolutions.

If you would like to be a 'test' case (don't worry, nothing here is permanent), we can try amending the boot process. For this to work, your Grub files need to be intact (which there is not reason to suspect they aren't), you need to know the Ubuntu partition, you don't have a separate /boot partition, and you have to be able to access the Grub menu.

At the Grub menu (hold down the SHIFT key if you don't see it), press 'c' to get to the command line. Then type the following. I will use sda1 as your Ubuntu partition, *but **change this** to the correct partition if it is not*. Don't type the # or what follows.

vbeinfo  # This will show allowable displays. I'll use 640x480 but you can use higher if desired and shown in the return.
```
set gfxmode=640x480
linux /vmlinuz root=*/dev/sd**a1*** ro
initrd /initrd.img
boot
```
If this works we can make some of the changes permanent. If it doesn't, nothing you typed at the Grub prompt will be saved and the boot process will return to what you had previously.

---

