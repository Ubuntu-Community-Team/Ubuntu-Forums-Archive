---
title: "Help Instaling Windows."
date: 2011-07-16
forum: General Help
---

### Post by Feech on 2011-07-16
No matter what bootable i use Ubuntu seems t just load right up and i am not able to boot from CD to install onto a PC. I have tried everything it is 8am and i have been trying 9pm last night any help woul be very helpful.

THanks guys

---

### Post by Dbury5 on 2011-07-16
Did you change your BIOS to boot from the CD before the hard drive?

---

### Post by haqking on 2011-07-16
> **Feech said:**
> No matter what bootable i use Ubuntu seems t just load right up and i am not able to boot from CD to install onto a PC. I have tried everything it is 8am and i have been trying 9pm last night any help woul be very helpful.

THanks guys

you mean you are trying to install windows onto a machine where Ubuntu is installed ?

is your BIOS boot order set to allow booting from CD/DVD ?

---

### Post by gandaran on 2011-07-16
> **Feech said:**
> No matter what bootable i use Ubuntu seems t just load right up and i am not able to boot from CD to install onto a PC. I have tried everything it is 8am and i have been trying 9pm last night any help woul be very helpful.

THanks guys
did you login to BIOS and choose the cd/dvd drive as the first boot device?

---

### Post by Feech on 2011-07-16
Yes i want to put ubuntu on another PC and windows on this one and it is set to boot from CD/DVD first but it just brings up thr ubuntu welcome screen

---

### Post by haqking on 2011-07-16
> **Feech said:**
> Yes i want to put ubuntu on another PC and windows on this one and it is set to boot from CD/DVD first but it just brings up thr ubuntu welcome screen

is the CD/DVD definately a bootable version of Windows ?

Was it an ISO you burned ?

was it burnt properly ?

---

### Post by gandaran on 2011-07-16
> **Feech said:**
> Yes i want to put ubuntu on another PC and windows on this one and it is set to boot from CD/DVD first but it just brings up thr ubuntu welcome screen
then your windows disk should be the problem, maybe it doesn't have the boot files.

---

### Post by Feech on 2011-07-16
I tried it on another PC it bootd fine is there a way i can wipe this drive clean on Linux almost to a factory setting so i can install windows?

---

### Post by mastablasta on 2011-07-16
stick in linuxcd and boot from it then format the disk (this will erase all data).

if windows disk is not recognised during boto then this is windows CD probelm (perhaps this verison is not supported by motherboard? you could try one thing to unplug the disk and then boot only with CD drive inside. this will let you know more on the error.

---

### Post by Feech on 2011-07-16
u mean an actual ubuntu cd to erase and when it done pop in yhe windows cd?

---

### Post by gnush on 2011-07-16
> **Feech said:**
> I tried it on another PC it bootd fine is there a way i can wipe this drive clean on Linux almost to a factory setting so i can install windows?

Yeah.
```
dd if=/dev/zero of=/dev/sda bs=1M
```You'll have to boot a live cd containing Linux to run the command above, it'll overwrite the drive (sda, change it to the drive you wish to wipe) with zeroes.

---

### Post by Feech on 2011-07-16
This linux stuff is confusing, Don't get me wrong i just don't understand it and a lot of my programs/games so not work even with Wine

---

### Post by gandaran on 2011-07-16
> **Feech said:**
> I tried it on another PC it bootd fine is there a way i can wipe this drive clean on Linux almost to a factory setting so i can install windows?
which windows service pack is on the windows disk? you may have problems booting some older windows service packs from disk on sata hardware as you will need to load sata drivers from a floppy drive before you can boot and install windows.

---

### Post by Vahe Nersesian on 2011-07-16
Have you tried to enter your boot menu, and choose the DVD which contains windows. you don't need to enter BIOS and change the boot sequence only during starting press F<n> n=any which will be displayed on your screen.

---

### Post by Feech on 2011-07-16
i put the same exact cd in another computer and it booted fine (Press any key to boot from CD...) but here with ubuntu it goes right to ubuntu startup screen to login.

---

### Post by todak on 2011-07-16
Maybe your cd/dvd drive is bad. Swap it for a known good one and try booting the disk again.

---

### Post by gandaran on 2011-07-17
> **Feech said:**
> i put the same exact cd in another computer and it booted fine (Press any key to boot from CD...) but here with ubuntu it goes right to ubuntu startup screen to login.
that has nothing to do with ubuntu, it should boot just as well as in the other computer, check if the other computer has IDE hardware and yours uses SATA hardware, if this is the case then try with windows 7, vista or windows XP service pack 3, any of these can load SATA drivers and boot on your computer.

---

### Post by mastablasta on 2011-07-18
> **Feech said:**
> u mean an actual ubuntu cd to erase and when it done pop in yhe windows cd?
 
Sure. it this is not a sata driver issue or CD/DVD drive issue as mentioned above...
 
> **Feech said:**
> This linux stuff is confusing, Don't get me wrong i just don't understand it and a lot of my programs/games so not work even with Wine
 
It's just different. it helps if you read a bit about it first. just to learn some basics. most of the internet runs on linux. so somehting must be good about it.
 
it helps if you already used opensource programmes in Windows (for example firefox, thunderbird, gimp) they are the same in Linux. transition is much easier. many programmes have their linux alternatives. some have even more alternatives and some alternatives are much better, while oters not so good. some sepcific/specialised programmes only have Windows and Mac OS verisons.
 
Games are not that well covered in Linux as developers don't find it profitable to make it for linux. at least not yet. So they often make them specifically for Windows. and they won't work in any other PC operating system eventhough it says PC-DVD on thei cover :-)

---

