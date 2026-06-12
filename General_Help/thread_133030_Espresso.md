---
title: "Espresso?"
date: 2006-02-19
forum: General Help
---

### Post by fladd on 2006-02-19
Hello,

I am just worying about the merging of the install and live cd into one cd.
I know this livecd installation from knoppix and kanotix already which i used before. My actual question is: Is there any qualitative difference in the installed system you get? With Knoppix/Kanotix I always felt a bit strange of having a livecd running on my harddisk. Isn't a "normal" installed system better configured and better fitted to the machine? I mean is there any disadvantage of copying a livecd to a disk in regard to a "normal" installation? And furthermore, how to install packages on the cd using apt-get? Would be difficult I guess. The same with upgrading.
So if anyone has anyknowledge about the quality of livesystem installers, please share it :-)

Regards
fladd

---

### Post by fladd on 2006-02-20
Any thoughts anyone?

fladd

---

### Post by bjweeks on 2006-02-20
Its the same just easier. It doesn't copy the cd it installs it just like before. It is still a "normal" install. Your can't install packages onto the cd. Upgradeing will be the same as before. After you remove the cd the install is still the same.

---

### Post by az on 2006-02-20
[QUOTE=fladd]Hello,
Isn't a "normal" installed system better configured and better fitted to the machine? 
fladd[/QUOTE]

To make a live cd, you take an installed system and compress it and make its init scripts capable of booting from disk and running from memory.

The Install permanently (Espresso) scripts undoes that process, installing the actualy system back onto your hard drive.

You end up with a normal Ubuntu system that is installed realy quickly.

---

### Post by fladd on 2006-02-20
Okay, but if an installed system is compressed for a live cd, and then the whole process is reverted for copying it to my harddisk, how is it then configured to fit my system? During a "normal" installation this is done, because the packages you need are installed, but how does that work with a livecd installer? If I take the Dapper install cd and install it, will it be exactly the same as the installation of the Dapper live cd?

Regards
Florian

---

### Post by az on 2006-02-20
[QUOTE=fladd] but how does that work with a livecd installer? If I take the Dapper install cd and install it, will it be exactly the same as the installation of the Dapper live cd?

Regards
Florian[/QUOTE]


The live installer configures your video hardware during boot.  Your username, password and mountpoints are configured by the installer (espresso).  All the other hardware is probed at boot as usual.

It will be exactly the same as a regular install.

---

