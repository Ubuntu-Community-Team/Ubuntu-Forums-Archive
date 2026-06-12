---
title: "what just happened??"
date: 2006-05-03
forum: General Help
---

### Post by Vlatko on 2006-05-03
i tried installing linux on my old machine this time, instead of the new one, so i can take my time and learn before installing it, again, on the new one.

so i went on and installed xp first, everything went well so i decided to go and install ubuntu. i have 2 hard disks, one 40gb for windows and the other 20gb for ubuntu. so i did everything necessary, partitioned the 20gb hard drive and everything was going fine, it seemed so anyway. but....
i got a following error, while installing the base system:
**debootstrap program exited with an error (return value 1)**

i googled that error and most people seemed to have said that was a badly burned cd. ok, ship it sent 3, i'll try one else, i know for a fact i installed from one on my new pc.

but now the problem is i can no longer boot from any of the 3 ubuntu cds!! everyone gives me the "insert system disk and press enter error"

i can still boot in my windows installation but i can't boot from the ubuntu cds anymore?? ](*,)

---

### Post by jimbren on 2006-05-03
Not to sound like an ***, but are you sure you're trying to boot from the CD?  I did something similar a while back, thinking I had set the bios to boot from CD, when in fact I set it to boot from a second, non-formated drive.

---

### Post by Vlatko on 2006-05-03
[QUOTE=jimbren]Not to sound like an ***, but are you sure you're trying to boot from the CD?  I did something similar a while back, thinking I had set the bios to boot from CD, when in fact I set it to boot from a second, non-formated drive.[/QUOTE]
100% sure. i went and checked that first. cd-rom boot was the only enabled, hd disabled and i don't have any floppy drives.


i forgot, if that means anything to you. i tried repeating installing the base system about 3 times when something happened and i saw a command something like **"syskill", computer will now reboot.**

---

### Post by cgjones on 2006-05-03
Not sure if this would make any difference, but I wouldn't completely disable the ability to boot from the hard drive, just set if to boot after the cd-rom.

---

### Post by Vlatko on 2006-05-04
[QUOTE=cgjones]Not sure if this would make any difference, but I wouldn't completely disable the ability to boot from the hard drive, just set if to boot after the cd-rom.[/QUOTE]
i just checked and i can boot with all my system disks and various linux distros, plus xp disc but i can't boot with ubuntu cd's any more. i can boot with kubuntu as well.

what could have made this?

---

### Post by cgjones on 2006-05-04
If you can boot from all those other CD's, but not the Ubuntu ones, the Ubuntu CD's must be bad. I honestly have no idea how 3 CD's would all go bad like that. If you can, download the Ubuntu install ISO and burn it to a CD. Then try to install from the new CD.

---

### Post by Vlatko on 2006-05-04
i seriously have no idea. i am trying a kubunut installation now and i have a problem with installation... ( it asks me for a name, user name and password and when i do it asks me for it again!! i already entered it for like 5 times!!!

---

### Post by cgjones on 2006-05-04
The installer should only ask for the password twice. Is it asking for all 3 of those things (full name, user name, password) many times, or just the password? Also, I hadn't thought of this before, but you could do a base (server) install of Kubuntu, then install the Ubuntu desktop. If you want to try this, let me know and I'll get back to you with the specific commands you'll need. Depending on how comfortable you are with the command line, this way of getting Ubuntu installed will be kind of tricky. But it's worth a try.

---

### Post by Vlatko on 2006-05-04
it asks me for a full name, user name and a password. password i enter once, than again to vreify. i do it, and aftre the verification the same screen appears and it asks me for the full name, user name and password all over again!!

i just tried all my ship it cds(ubuntu) on my new pc and they all work. the installation starts but on the old one i get a insert system disk error.

p.s.i'm a complete noob so i'm not confortable with the command line at all, but thanks. ;)

---

### Post by cgjones on 2006-05-04
This one has me stumped. I would almost tend to think that it's something with the hardware, but other CD's will boot. I'll try doing some research on it. Hopefully we can figure something out. Just out of curiousity, could you post the specifications of both computer here. I want to get an idea of any hardware differences between the two.

---

### Post by Vlatko on 2006-05-04
sue thing.
new pc:
amd 64 athlon 3500+
abit an8 sli
1gb ram
6600 gt 128mb
wd sata caviar 250gb
seagate ide 120gb
dvd/rw _nec

old pc:
pentium 1200mhz
512mb
asus tusl-2c
radeon 7500 64mb
seagate ide 40gb
seagate ide 20gb
dvd/rw _nec

---

### Post by cgjones on 2006-05-04
What Ubuntu CD's do you have? Do you have 3 different CD's (i386, x86_64, PPC), or 3 of the same kind?

---

### Post by Vlatko on 2006-05-04
[QUOTE=cgjones]What Ubuntu CD's do you have? Do you have 3 different CD's (i386, x86_64, PPC), or 3 of the same kind?[/QUOTE]
i have 3 i386 and 2  x86_64.. the cds aren't the problem i think, cause they all work on the new pc.

---

### Post by Vlatko on 2006-05-04
btw, i just managed to install kubuntu. seems the reason for repeating me to enter myusernmae was cause my /home partition was set to fat32. when it should have been to ext3.

source: [http://ubuntuforums.org/showthread.php?t=37384](http://ubuntuforums.org/showthread.php?t=37384)

---

### Post by cgjones on 2006-05-04
I asked which CD's you had because I wanted to make sure that you weren't trying to install the x86_64 version on the older computer. How are the hard drives and DVD drive layed out? Yeah, your home partition should be on a Linux native partition (ext2, ext3, reiser).

---

### Post by Vlatko on 2006-05-04
> I asked which CD's you had because I wanted to make sure that you weren't trying to install the x86_64 version on the older computer. 
i'm not such a big noob. :D
> How are the hard drives and DVD drive layed out?
 if you mean how the drives are connected, i'ts like this:
**primary ide master:** seagate 40gb, partitioned to one of 10gb with windows and the other 30gb for stuff, both ntfs.
**primary ide slave:**dvd/rw nec
**primary ide master:**:nothing
**secondary ide slave:**: seagate 20gb, with linux

---

### Post by cgjones on 2006-05-04
I've heard of people having problems when they have an optical drive and a hard drive on the same IDE. I'm not sure that applies to this case, because the other CD's will boot just fine. You might want to try putting both hard drives on the primary IDE, and put the DVD/RW on the secondary IDE. Also, you state that the Seagate 20GB is slave on the secondary IDE. I'm pretty sure that it's not physically possible to have a slave without a master. Is this drive jumped as slave? And which IDE connector is it plugged into, the middle one or the end one?

---

### Post by Vlatko on 2006-05-04
[QUOTE=cgjones]I've heard of people having problems when they have an optical drive and a hard drive on the same IDE. I'm not sure that applies to this case, because the other CD's will boot just fine. You might want to try putting both hard drives on the primary IDE, and put the DVD/RW on the secondary IDE. Also, you state that the Seagate 20GB is slave on the secondary IDE. I'm pretty sure that it's not physically possible to have a slave without a master. Is this drive jumped as slave? And which IDE connector is it plugged into, the middle one or the end one?[/QUOTE]
it is connected to the end one. and it is set to slave cause i don-t have a jumper for it. its my oldest drive and i misplaced it some time ago.

btw, i wrote this in kubuntu. it looks sooooo cool. :D

---

### Post by cgjones on 2006-05-04
Having that 20GB drive jumped (or not jumped, as the case may be) as slave by itself on an IDE chain might be part of the problem.

---

### Post by Vlatko on 2006-05-05
[QUOTE=cgjones]Having that 20GB drive jumped (or not jumped, as the case may be) as slave by itself on an IDE chain might be part of the problem.[/QUOTE]
i don't think it is cause i used it like that always. i lost a jumper so it can only be set as slave. but all other disks boot. just the ubuntu ones don't. all of this ever since i got a error during a installation **"debootstrap program exited with an error (return value 1)"** then the installation aborted and the pc restarted and the ubuntu cd's are no longer bootable.

---

### Post by cgjones on 2006-05-05
I'm running out of ideas. But you've got Kubuntu installed, and you like it? Well, good luck with it, and I hope it works out.

---

### Post by Chasehead on 2006-05-06
the same thing happened to me on my toshiba craptop.

I got that same problem very briefly but i managed to solve it just by rebooting into windows, shutting down, and restart with the ubuntu cd in the drive. it all worked fine after that.

if you do get it working, try deleting all the partitions in the installer except the windows one, and use ext3. I am also extremely new at this so take my advice with a grain of salt.

good luck!

---

