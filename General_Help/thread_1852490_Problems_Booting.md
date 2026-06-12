---
title: "Problems Booting"
date: 2011-09-30
forum: General Help
---

### Post by mightyseaking on 2011-09-30
Hi all,
I have been for several days now trying to install ubuntu desktop version 11.04 64bit
to no avail.
My first problem is when I switch on the computer I get a purple coloured screen (the grub colour) but blank then the system reboots.
After the computer has done this first screen the grub menu shows with the default four options.

If I hit enter on the top option it boots to intramfs prompt  so i try the command mount /dev/sda1/
which comes back and says there is no such directory in the fstab 

If i switch to the second option in grub it will boot to the command prompt. from where i can restart the gnome desktop and it works.

I have gone into the /boot/grub/ directory and edited out the root=uuid=(blah blah blah) and changed it to root=/dev/sda1/
this still doesn't work.

If I install opensuse  (should I mention that here)  lol then the system boots perfectly...
but i have spent the last few days learning ubuntu and commands on a spare laptop  hence why I would prefer to use ubuntu

my instinct is that grub is trying to load before the sata disk is recognised  and timesout or something along them lines...

any replys are greatly appreciated I am fairly new to linux however very computer literate , 

I should also mention that I have reformatted and partitioned the drive default and done a default installation and still no joy

---

### Post by 2F4U on 2011-09-30
Recent versions of Ubuntu use grub2. If you edit /boot/grub, these changes are overwritten. Instead, you should edit

**/etc/default/grub**

and after your editing is finished, call 
[B]
sudo update-grub [/B]

to make the changes permanent.

---

