---
title: "Kubuntu LiveCD is kuber-slow (and other tales of misfortune)"
date: 2006-06-15
forum: General Help
---

### Post by Zeroangel on 2006-06-15
Hi all,

I recently burnt a Kubuntu CD (the standard 386 styling) and tried to run it on an AMD Duron machine, well for starters I noticed a little multicolored graphical glitch line when the 'starting' dialogue box popped up and the machine went into normal bootup, the CD drive was acting strangely especially how the CD light blinked, so I replaced the CD drive, then I replaced the IDE cables and it still went slowly (but slightly faster) finally it booted and I got a semi desktop, waiting 4 minutes later I recieved a warning that there was an error with the desktop and it had crashed. Then I got errors from the panel saying that protocol 'system' was not understood. OK fine. I tried working around that, doing things like opening Konqueror (it took a blazing fast 6 minutes!) running kdesktop& from the console (it worked, but only 10 minutes later and with an error message saying that there was something wrong with input device 156 0x00) and finally running the 'install' shortcut. No good, 1 hour later and the CD drive light was still flashing away.

I tried on another machine and it worked! It took 5 minutes to bootup, and everything worked, not bad for a liveCD.

So what is it with the first machine? Its an AMD Duron with 128MB of PC-133 RAM, a fairly standard machine, I mean Windows 98 works just fine on it, but why won't Kubuntu? Does anyone know how I might find and fix the problem that prevents Kubuntu from working properly on it?

Thanks.

---

### Post by Doytch on 2006-06-15
How much RAM does the other computer have?

---

### Post by eth on 2006-06-15
and...what video chipset has it got?

---

### Post by Zeroangel on 2006-06-15
The problem computer has 133MB of RAM and an ATI Rage XL videocard, the motherboard chipset is A7V-E (sounds like an ASUS chipset, but not sure). The working computer is Pentium 4 with 506MB of RAM.


On another problem (not sure if its relevant) I've installed Ubuntu Breezy on it before, but noticed that it would lock up or misbehave after some I/O instensive operations, or during the dist-upgrade, or the the CD drive would refuse to eject any disks under breezy, then I rebooted and got a SMART warning that the HD was failing, so I replaced the HD and IDE cables and tried to install Kubuntu Dapper on it. I am not getting any SMART warnings with the new HD, but I just thought it would be worth mentioning.

---

### Post by eth on 2006-06-15
The Live CD/DVD is built to run on a machine with at least 192MB of RAM...try the Sever edition, and install the X server via apt-get using fluxbox, it should work

---

### Post by bruce89 on 2006-06-15
I think [Xubuntu]("http://www.xubuntu.org") would be a better bet.

---

### Post by Zeroangel on 2006-06-15
[QUOTE=eth]The Live CD/DVD is built to run on a machine with at least 192MB of RAM...try the Sever edition, and install the X server via apt-get using fluxbox, it should work[/QUOTE]
Thanks! :KS 

I added another stick of RAM in and the LiveCD runs as smooth as butta. :)

---

