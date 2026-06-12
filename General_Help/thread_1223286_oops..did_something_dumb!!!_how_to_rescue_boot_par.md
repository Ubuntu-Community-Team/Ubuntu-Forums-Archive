---
title: "oops..did something dumb!!! how to rescue boot partition or completely erase my hdd?"
date: 2009-07-26
forum: General Help
---

### Post by agingric on 2009-07-26
hi folks,

i have been having some problems with my laptop crashing as of late.  it had been happening in both windows xp and jaunty.

fortunately, before i began experimenting, i backed up all data that i wanted to keep on flash drives.

too bad i did not look at the forums or ask before i did what i did, as i see it could have been easily avoided with some proper planning.

i used the recovery dvd that came with the computer, thinking that it would restore my hard drive to "new" condition.  much to my surprise, when i turned it on after running the cd the grub boot loader came up.  this is where i made my big mistake.  i deleted my ubuntu partitions, and of course i am getting 

grub boot loader error 22, when i turn on the machine.

i looked at forums and saw that i could fix my mbr by using the windows dvd (have not been able to figure out a way to get to mbr with this disc) or my ubuntu cd (it's intredpid, i upgraded to jaunty later and don't have disc for it) could download one if neccessary.  i have not been able to figure out how to do it.

what is the best/easiest way to access the mbr?  can it be done or must i wipe out the hard drive with another program and start fresh?  i am willing to do that and run the windows dvd again afterwards.

any help would be appreciated!
thanks
andy

---

### Post by darolu on 2009-07-26
You can try restoring your partitions with gparted; boot from the CD/flash drive and install gparted; restore your partitions with it (is really easy to use), make sure you flag your booting partition (right click flag as bootable); after that you can restore GRUB the way you read.
If you formatted the HD, then you will have to re-install Ubuntu.

---

### Post by SKeaLoT on 2009-07-26
alternatively, you could pop-in your windows dvd, go to a recovery console and run the "fixmbr" and "fixboot" commands... i would go for the other solution though

---

### Post by agingric on 2009-07-26
trouble was i could not figure out a way to bring up the recovery console from the windows dvd.

and did not see anything about grub in gparted (i already have a disk for gparted).  

might need a little more guidance...

if it would come down to reformatting my hard drive, could it be done with gparted?  or would i need a different program?


thanks :)
andy

---

### Post by darolu on 2009-07-26
Grub is a different thing than gparted, with gparted you can set your hard drive partitions, you can format hard drives with gparted too.
To fix grub, first you need to have both OS's installed (grub is a boot loader), you can follow this steps: [http://ubuntuforums.org/showpost.php?p=7667550&postcount=2](http://ubuntuforums.org/showpost.php?p=7667550&postcount=2)

Or (considering you said you backed up your files) you can just re-install Ubuntu, be careful when setting your partitions (you will need to do it manually).

---

### Post by agingric on 2009-07-26
using the ubuntu live cd sounds great, but my copy of intrepid doesn't seem to have a live option, just regular install?  am i missing something?
thanks,
andy

---

### Post by agingric on 2009-07-26
bump

---

### Post by apparle on 2009-07-26
I have a simple option [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Download, burn and then boot from this disc.
It has and option to boot from windows and plus fix the mbr to always boot from windows
Select the option 'WIN => MBR & !WIN!' when you get the screen below
[http://www.linuxplanet.com/graphics/screenshots/GrubDisk2.jpg](http://www.linuxplanet.com/graphics/screenshots/GrubDisk2.jpg)

---

### Post by zarqoon on 2009-07-26
If you want to install ubuntu again just do that and it should reinstall grub and make your windows available.
If not you can enter fixmbr and fixboot in the recovery console.
But to get into that you need a regular windows install cd. During xp install there is a point where it asks you to press enter to begin install, f3 to abort or r to enter the recovery console. It could very well be that your recovery cd does not do that.

---

### Post by agingric on 2009-07-26
thanks...

clicked on that and it says:

"Connection Problems
Sorry, SMF was unable to connect to the database. This may be caused by the server being busy. Please try again later."

are there any other sites that have the same program available for download or should i just give it some time and hope that the link works later? 

thanks,
andy

---

### Post by agingric on 2009-07-29
well, i wound up using darik's nuke to wipe out my hard drive.  

re-installed windows xp using the recovery disk that came with the computer.

still crashing randomly with a fresh install of windows.  has not crashed in safe mode.

no doubt this is a hardware issue.  is there any means by which i can diagnose at home?  i could take it to my "guy" later this week, but would like to figure out what it is beforehand and if it is worth having looked at.  i only have limited experience with computer repair (installing memory or a hard drive is about it.)  

i have tested the memory with memtest 86 and it passed.

for now i am happy to have a computer i can use.  will not be doing anything critical or saving anything important on this machine till this issue can be resolved.  



it just went out again.  when it booted itself back up i got an error about the toshiba power saver.  

if anyone could give me some pointers, i would greatly appreciate it.  if i can restore this machine to proper working order or have to wind up buying a new laptop i will be installing ubuntu again.  i miss it quite a bit already!

thanks much
andy

---

