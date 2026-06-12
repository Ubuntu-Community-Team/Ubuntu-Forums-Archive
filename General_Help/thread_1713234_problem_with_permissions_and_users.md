---
title: "problem with permissions and users"
date: 2011-03-23
forum: General Help
---

### Post by mighty_wolf on 2011-03-23
Hi, recently i logged in ubuntu by the root user and i opened a terminal at the / directory. I changed mode as follows

>  chmod -R 700 * 

I shuted down ubuntu. At next day the following message box appeared on the screen before logging in ubuntu :

> There is a problem with the configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

The login page was shown in a very failsafe mode. Icould login only by root. i logged in and i changed the permissions at / directory like this:

>  chmod -R 777 * 

I restarted and i logged in. I could enter to any user everywhere and ubuntu are now fully functional. The problem is that when i go on system->administration->users and groups, a message box appears saying :

> The configuration could not be loaded

An unknown error occured

So, I want to fix this problem and also i want to know an easy way to grant permissions on specific users ONLY by the root user (I think it is done by SUDO command but i need a useful guide to do this with many examples to understand this essential command. If it is not the command i want, Iam all ears for new ideas. ;) ).

Thanks in advance

---

### Post by rmemm on 2011-03-24
I'm assuming that you mean that you changed the permissions on every single file, directory, device, symbolic link etc on your system?  Is that what you mean?  If so why?

If this is in fact what you did, I would either restore from backup or reinstall.  There is no easy way to reset all permissions everywhere correctly.  It's just too complex.

For example -- consider that you probably changed also the SUID and SGID attributes of some resources and executables, the Sicky bit on others.  File permissions are more than just read-write-execute.  It's a real mess.  You'll be tracking these down forever unless you restore or reinstall.

Rob

---

### Post by mighty_wolf on 2011-03-24
ok! So what can i do to fix the current problem or if it cannot be done how can i reinstall ubuntu without changing anything in the operating system. What iam asking is if there is something like repair! 

Thanks a lot

---

### Post by falko on 2011-03-24
I'm afraid you have to back up your important files (documents, etc.), reinstall from scratch and then restore your files.

---

### Post by mighty_wolf on 2011-03-24
Ok i will do this but i need  to ask something else! I have dual boot with windows xp prof sp2. If i reinstall ubuntu will this affect windows or boot sectors?

---

### Post by Lars Noodén on 2011-03-24
> **mighty_wolf said:**
> Ok i will do this but i need  to ask something else! I have dual boot with windows xp prof sp2. If i reinstall ubuntu will this affect windows or boot sectors?
Ubuntu is usually pretty good about finding the other systems you might have.  Be sure to back up you data on both systems before you re-install.  FWIW, it was the chmod 777 that zapped your machine.

---

### Post by mighty_wolf on 2011-03-24
well i have really really big problem

I cannot access through usb my movable hard disk. How can i make ubuntu to detect it in the current situation

---

### Post by rmemm on 2011-03-25
You know I had that problem -- i.e. could not mount usb drive from the boot CD.  I don't know why.  I ended up backing up over the network to another machine.  Other option -- if you can see the partition of the usb drive listed in /proc/partitions, then you might be about to manually mout it with the "mount" command.  Another option is to used an alternate boot CD or media -- like puppy linux or one of the other small linux distros.

Rob

---

