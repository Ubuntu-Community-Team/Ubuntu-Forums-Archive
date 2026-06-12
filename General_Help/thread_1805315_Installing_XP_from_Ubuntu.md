---
title: "Installing XP from Ubuntu"
date: 2011-07-15
forum: General Help
---

### Post by abc123def456 on 2011-07-15
Hello there (:. I have a Hp G60-530us laptop and it came with Windows 7, then I decided to switch to Ubuntu and kept it for a while. Now I have an XP disk and decided to try switch OS's to XP. I backed up what files I wanted and then basically restarted the computer (that is all I did to prepare to install XP by the way), hit F10 to access some settings where I changed the boot order to boot from the CD, and a blue Windows Setup screen came up. I let it run until it said starting windows...then the screen came up saying:
"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer *(I did and received the same error screen)*. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated.
Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:
*** STOP: 0x0000007B (0xF78D2524, 0xC0000034, 0x00000000, 0x00000000)"

I am essentially a n00b when it comes to these things, so any help would be greatly appreciated.
Thanks in advance,
Michael

---

### Post by aktiwers on 2011-07-15
It has nothing to do with Ubuntu. Windows XP would do this if Ubuntu was there or not.

[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

Most likely you can boot into bios and change the controller interface for you harddrive. Switch it to ATA. Or you need to download the SATA drivers and put them on a .. *sigh floppy disk and load them in before the install.

---

### Post by pqwoerituytrueiwoq on 2011-07-15
haha windows bsod before it could even get on the computer
sorry could not resist

anyway make sure the disk was burned properly 

you could always shrink Ubuntu with gparted and make it a duel boot

why not just run xp in a virtual box
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
just substitute windows for Ubuntu and vice versa
you can search virtual box in the software center

you would have better luck a a windows forum for this one for installing in the the laptop like you are trying now

---

### Post by szal on 2011-07-15
> **pqwoerituytrueiwoq said:**
> anyway make sure the disk was burned properly
That would imply using an illegitimate copy…

Btw, sentence marks (e.g. full stops) exist for being used. :P

---

### Post by aktiwers on 2011-07-15
> **szal said:**
> That would imply using an illegitimate copy&#8230;

Btw, sentence marks (e.g. full stops) exist for being used. :P

Why are people so nazi about legal copy's? You can easily have Windows ISO's that are legal. MSDNAA provides free downloadable Microsoft software for students on many Universities. Business' who legally pay also get access to downloadable ISO's, and in many cases also pay for their employees copies. 

Why assume he implied an illegal copy? I would rather assume he read the rules and help out  ;)

---

### Post by wildmanne39 on 2011-07-16
Hi, I believe to install xp because it is an older version of windows you need to boot from a livecd of ubuntu and if you are sure you want to get rid of ubuntu format the paritions to ntfs or fat 32 and then xp should be able to install assuming there is no other problem.

---

