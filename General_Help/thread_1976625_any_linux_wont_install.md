---
title: "any linux wont install?"
date: 2012-05-09
forum: General Help
---

### Post by gene simmons on 2012-05-09
hi all,i recently purchased a acer d270 netbook,upgraded the ram to 2g,i got rid of windows starter and installed windows7 profesional,i want to dual boot with linux,i have used linux for years on my other pcs,i have many diferent distros and they all boot fine with usb or on dvd,i cant get any to work on this pc,i burn a distro on unetbootin on a diff pc and it boots fine but on this pc i get errors,bad target numbers and it fails to load,most distros will fail at sys linux and hang there,i tried a linux mint install as thats the distro i want to run and i installed mint for win and it seemed to go ok but after a reboot i get the same error with bad target number and it fails to load,goes to desktop pic and hangs there,mint shows up in the bootloader and i have tried every option in the menu and same thing,it wont load,i read others have linux instaalled fine on this machine,i cant for the life of me get it to install on mine,any sugestions guys,??

---

### Post by 2F4U on 2012-05-09
If any distro fails to boot it may be a hardware problem. Did you verify that the RAM is working by running memtest?

---

### Post by plant on 2012-05-09
Are you trying to install via usb?

---

### Post by drtheradio on 2012-05-09
Find out what video card you have 


 If you have Intel i915 graphics, try adding one of:

            i915.modeset=0

            i915.modeset=1 

        If you have ATI Radeon graphics, try adding one of:

            radeon.modeset=0

            radeon.modeset=1 

        If you have NVidea graphics, try adding one of:

            nouveau.modeset=0

            nouveau.modeset=1 

I had the same issue ..

all the cds let you edit the boot option Ubuntu is F6.

Try that......

---

### Post by gene simmons on 2012-05-10
thanx so much for the tips,i beleive its a intel 3600 series graphics card,i have tried using unetbootin on a diferent pc and make a bootable usb and i have tried a external dvd drive both with no sucess,so when i boot and it says sys linux and hangs there i cant seem to type anything where would i put the intel commands?can u gove me a step by step,again thanx so much for the tips,i like this little netbook but i want to run a light distro on it,thanx

---

### Post by pqwoerituytrueiwoq on 2012-05-10
so when you hit default in unetbootin's grub menu you get a couple lines then it seems to stop do in anything the same thing happens to me on my desktop with 12.04 i had to hit tab  on default and add [FONT=Courier New]nomodeset[/FONT] to the line, i put it between [FONT=Courier New]splash[/FONT] and [FONT=Courier New]quiet[/FONT]

---

### Post by Totouy on 2012-10-31
Hi [gene simmons]("http://ubuntuforums.org/member.php?u=1234132"), did you get to work it on the PC. I have the same error but even cant boot from the USB stick I mean only can load right now is the BIOS :(....

---

### Post by cmcanulty on 2012-10-31
I have an acer netbook and it runs ubuntu fine.

---

