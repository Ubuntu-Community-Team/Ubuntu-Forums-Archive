---
title: "ACPI 10.04LTS is driving me crazy!"
date: 2011-12-04
forum: General Help
---

### Post by kindledwind on 2011-12-04
I have a Dell dimension 3000 that I'm trying to get 10.04LTS & EMC2 running on. The first issue I ran into when loading the live CD is that it would power down the monitor on boot. Finally found the menu on F2 during boot, used F6 & shut acpi off which let the monitor remain lit long enough to install it.

So, 10.04 LTS is installed to the HD. But again, it shuts the monitor off as fast as it can. I haven't even seen Grub on this machine. I edited /etc/default/grub to turn ACPI off with the live CD, but I can't run update-grub due to no monitor.

SSH is bust too, can't see to install ssh server.... so now what? There are no BIOS options to disable ACPI.

todd

---

### Post by kindledwind on 2011-12-04
Discovered chroot. Installed vim & openssh server so far. I can access it from my netbook. 

Still can't keep it from shutting the monitor off though. Maybe it's not an ACPI thing? 

Any other ideas?

todd

---

### Post by L a r r y on 2011-12-05
Looking in Google, I came up with a Fedora Core 3 solution to turn off ACPI on the Dell Dimension 3000:

 
ACPI can be disabled by entering [FONT="Courier New"]**acpi=off**[/FONT]  in the lilo configuration file, then reinstalling lilo boot loader.

However, Ubuntu 10.04 does not use this boot loader.  

**Does anyone know** if ACPI can be turned off in the grub or grub2 configuration file?

I am not familiar with ACPI.

---

### Post by L a r r y on 2011-12-05
> **kindledwind said:**
> I have a Dell dimension 3000 that I'm trying to get 10.04LTS & EMC2 running on. The first issue I ran into when loading the live CD is that it would power down the monitor on boot. Finally found the menu on F2 during boot, used F6 & shut acpi off which let the monitor remain lit long enough to install it.

So, 10.04 LTS is installed to the HD. But again, it shuts the monitor off as fast as it can. I haven't even seen Grub on this machine. I edited /etc/default/grub to turn ACPI off with the live CD, but I can't run update-grub due to no monitor.

SSH is bust too, can't see to install ssh server.... so now what? There are no BIOS options to disable ACPI.

todd
On [LinuxQuestions.org is this thread]("http://www.linuxquestions.org/questions/ubuntu-63/add-acpi%3Doff-radeon-modeset%3D0-to-grub-permanently-915227/") adding acpi=off to Grub in a version 11.xx of Ubuntu.  This may solve your issue.

---

### Post by kindledwind on 2011-12-05
Larry-
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It says you can...

I finally got it conquered.

I took the long route, if I were to have taken the short route, this is how it would have worked:

Boot the live CD, fdisk -l to find the hard drive file system, mount /dev/sda1 (or whatever the hd is) to /mnt, chroot to /mnt, edit /etc/default/grub to have this line instead of the original:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

run update-grub, shutdown from the desktop, remove the live CD & power it back up. It should take someone 10 minutes....not 4 hours like me :-) It takes more time to figure out HOW to get it done than it does to figure out what to do!

And pci-noacpi isn't the right idea.

todd

---

### Post by L a r r y on 2011-12-05
Todd --
Good information!

Be sure to hit the Thread Tools link at the top of the page and mark it as Solved.  That will serve as a beacon to others looking for this solution.

Regards --  Larry

---

