---
title: "resolution problim?"
date: 2006-03-23
forum: General Help
---

### Post by noodle360 on 2006-03-23
ok so heres whats goin  on... some years ago i bought an Emachine T2042 with windows XP, i recently built a new computer and installed Uduntu 5.10, the install went great and i got it running smoothly, then i soon found a problim... my resolution was stuck on 640x480 and im used to bigger on my windows PC's... i have had problims with this computer in the past, but i just had to put the CD in and download the correct drivers for XP, but seeing as how i am now not using XP, then drivers do me alota good. i would really like it if some one could point me in the direction of the graphics drivers i need, and tell me how to install, as i am a "nOOb" to this Linux. (the reason i installed this is i heard it was relativly easy)  PLZ help!:confused:

---

### Post by Perfect Storm on 2006-03-23
Try with:
```
sudo dpkg-reconfigure xserver-xorg
```
Through here you can set resolution.

You might read this first: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by akiro.yamamoto on 2006-03-23
I did a little checking and
According to [**Intel's Site**](http://www.intel.com/support/graphics/sb/cs-010512.htm?iid=graphics+845main&) the Intel 845gl which is the Video Card on your mother board only supports 2D functionality. But it supports a Max resolution of 1600x1200.
Find the section of your /etc/X11/xorg.conf file that looks like my pic and manually enter the resoulutions you want.
If your comp has an AGP or PCI card a visit to [**PriceWatch**](http://pricewatch.com/m-37.htm) should yield an ideal NVidia card for basic 3D gaming ( It did for me ;) ).
Hope this helps.....

---

### Post by noodle360 on 2006-03-23
ok, so i took all advise, and checked it all beetween last night and this morning, then went away for a bit, and came back to do some more work and this is what i have figured out... when i installed Linux (did it like 3 times thinking it was a bad install) they never asked for my root password, and i cant change the file, unless im in root... i was a post about looking in the install log file or somethign and it wasnt in there... so any more sugestions?

also, on my "good" new computer i have a Radeon 9550, that i picked up cheap cuz im more or less poor, then i found out ATI and Linux arnt the best of fans... so untill i got more money, and this resolution problim fixed, ill just keep XP on here, then duel boot them....

---

### Post by Hairy_Palms on 2006-03-23
u should try this program
[http://john.fremlin.de/programs/linux/read-edid/](http://john.fremlin.de/programs/linux/read-edid/)
then just replace your monitor section with the one it generates and add the resolution to your screen section oh and just use sudo to run root commands

for example
sudo gedit /etc/X11/xorg.conf

---

### Post by noodle360 on 2006-03-23
well guys, idk what the hell i did (all i did was restart the damn think for like the 400th time) but something worked.... i didnt edit any files or anything, and Linux picked up a higher RES. and higher refresh rate... well even if it is temp. its cooler... so im happy, thanks all, :bows:

---

