---
title: "Please help me"
date: 2012-03-17
forum: General Help
---

### Post by Bigdady27 on 2012-03-17
Hey all,

I HAVE A BIG PROBLEM!

I was win7 user since it came out, then i wanted to try out something new so i installed ubuntu, but i didnt know that i cant really play game's without installing some special addons ...etc
so now i would like to go back to win7 and this is where my problem starts.

I have Win7 folder and inside win7.iso file.

Can someone please tell me how to make that bootable DVD ?

I used like 4 DVD already and none of them works. Do i have to extract that iso file and then burn it ? Or do i just burn whole iso file on dvd ? What program to use to burn ? Any instruction's ? 

Please help me with this, i spend like 10 hours just to get this working.

Cheers

---

### Post by Bigdady27 on 2012-03-17
Bump !!!

---

### Post by winh8r on 2012-03-17
Have a look at this and see if it helps you:

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")
 
this is for basic .iso burning

OR look here for more specific help for your issue:

[http://forums.techarena.in/operating-systems/1174622.htm]("http://forums.techarena.in/operating-systems/1174622.htm")

Hope this helps you.

---

### Post by IWantFroyo on 2012-03-17
1) Insert a blank CD/DVD into your disc drive. Your disc drive must be able to burn, though.

2) Open Brasero, select "Burn Image", select the ISO inside of the program, and hit burn.

3) Once it's done, reboot your computer, and hit the key to enter setup. Once in there, go to "Advanced BIOS Options", and make your disc drive the first booting device. Save and exit.

4) Boot off the drive, and install Windows. Good luck!

---

### Post by Mark Phelps on 2012-03-18
It's likely that the Win7 ISO will require a DVD, not a CD, as the actual one does not fit on a CD.  So, you need to be sure that your optical drive can burn DVDs,  not just CDs.

Also, since Windows doesn't understand Linux filesystems, if the Linux filesystems are still on the drive when you boot the Win7 DVD, it may not see the hard drive.

Best approach would be, after you have the Win7 DVD made, to boot from an Ubuntu desktop CD, select Try Ubuntu, open the GParted app -- and delete all the partitions from the drive.

Then, when you reboot, Win7 should install OK.

---

