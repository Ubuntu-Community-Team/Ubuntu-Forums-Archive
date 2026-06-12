---
title: "Added HDD, Ubuntu no longer boots :("
date: 2006-02-02
forum: General Help
---

### Post by themole22 on 2006-02-02
Hi all,

I installed Ubuntu on my fileserver (with a Rocket 1540 controller, but without any drives attached).

It worked fine, everything was good, then I added a new WD2000JD to the controller and Ubuntu now hangs on boot at the Loading Modules screen (just after the graphical boot loader starts).

I can boot the live dvd, and see the new HDD including partition info etc, so I tried reinstalling and had exactly the same problem on first boot.

Any ideas?

Thanks,

Phil

---

### Post by WinCtrlAltDel on 2006-02-02
if you have two HDD on one ribbon cable you need to have one jumper set to master and one set to slave. Did you do this?

---

### Post by WinCtrlAltDel on 2006-02-02
.

---

### Post by dhjohnson on 2006-02-02
Yeah--sounds like a master/slave problem.  Check your jumpers and cables and let us know.

---

### Post by themole22 on 2006-02-03
Its a SATA drive, so no Master/Slave jumper woes.

Also, its visible/working in both WinXP and Ubuntu Live DVD, its only when I actually install Ubuntu that it causes the problem!

---

### Post by ockertom on 2006-02-03
Have you told the bios to boot from thate drive? Nix reads its shit from the bios, if its looking for normal drives no prob, but sata need to be added basically. Did this help?

---

### Post by themole22 on 2006-02-03
Nope, its an extra (non-motherboard) card, and the HDD doesn't have any partitions on it at the moment.

It starts booting, its just when it actually notices the HDD that it all breaks :(

The annoying thing is that the live disc works - what changes between running off the disc and running off an installed copy that could cause it to fail?

---

### Post by themole22 on 2006-02-03
OK, having started it in recovery console with and without the drive in, it seems as though its not initialising /dev (the next step in the boot sequence) when the drive is in. It also doesn't assign the extra IDEs, so maybe its something to do with the controller (Highpoint Rocket 1540). I am using the drivers included with Ubuntu, which seem to work on the live disc.

Hopefully this'll help, I'm tearing my hair out here :-k

---

### Post by dcstar on 2006-02-03
[QUOTE=themole22]OK, having started it in recovery console with and without the drive in, it seems as though its not initialising /dev (the next step in the boot sequence) when the drive is in. It also doesn't assign the extra IDEs, so maybe its something to do with the controller (Highpoint Rocket 1540). I am using the drivers included with Ubuntu, which seem to work on the live disc.

Hopefully this'll help, I'm tearing my hair out here :-k[/QUOTE]
Ubuntu "hard codes" the install drive designation when you first set it up.

If you add another drive after initial install, it is possible that the designation that Ubuntu assigned to the original drive may have changed, and this will cause problems.

This has also occurred when people have moved an IDE drive between the Primary and Secondary IDE channels, or swapped from Master to Slave.

Ubuntu assigns its first **detected** IDE device as hda (Master), hdb (Slave) and then the next detected devices are hdc and hdd.

If these designations changed after install, then Ubuntu will barf (I have seen a post on how to change this without a complete re-install, you may want to search for it).

If your SATA drives caused a similar change, it could explain your situation.

---

### Post by themole22 on 2006-02-13
OK, after a lot of digging, I've found out that the Highpoint drivers for the specific revision of card I have (the non-RAID R1540) are definitely buggy on any kernel after 2.6.10, which is why I can't compile the drivers after booting without the extra drives installed. In addition, the built in driver for the chipset causes the kernel to hang on boot ([http://bugme.osdl.org/show_bug.cgi?id=2555](http://bugme.osdl.org/show_bug.cgi?id=2555)) unless you use noprobe. However, I can't use noprobe, because the drives on the controller are assigned drive letters out of range for noprobe (all the way up to hdo1).

Even if I do manage to shuffle drives etc to get them noprobed, I still will not be able to use my drives because of the aforementioned driver problem.

The one thing, really, that gives me hope (and frustration, in equal measure) is that using the liveDVD, not only can I boot the system with the extra drives, but I can mount them and view the files on them through the terminal (I put an NTFS filesystem on them through WinXP, though it appears that I can change that with GParted, as it seems happy enough looking at the drives).

This is really strange behaviour, and I can't think of a single explanation. However, if any of you can come up with a way for me to get EVMS working on the liveDVD (ideally by making a new image with at minimum EVMS-CLI installed, preferably EMVS-GUI + dependencies) but even just a way to fire it up after using the default livedisc would be good (can't use apt-get, because for some unknown reason it thinks that archive.ubuntu.com is on 1.0.0.0, synaptic just hangs presumably with the same problem. I'm guessing this is a deliberate thing to stop people doing the admittedly slightly silly thing that I'm trying to do, installing new packages to an install that will vanish on reboot).

Thanks,

TheMole22

---

### Post by erthian on 2006-03-13
Having the same problem.... I just added a 160gb WD sata drive.  I made sure raid was disabled, tried running it with and with out jumpers set on the sata drive, tried it on two different sata channels, and even tried setting different jumpers on my ide drive.

I am booting off of a scsi drive, but I get the same errors.

running breezy 32bit on an AMD 64bit proc
Chaintech VNF4/Ultra Motherboard

---

### Post by erthian on 2006-03-14
If any one is still folowing this, I found the solution here: [http://www.ubuntuforums.org/showthread.php?t=80520&highlight=added+sata](http://www.ubuntuforums.org/showthread.php?t=80520&highlight=added+sata)

I simply renamed the device when grub was booting from sda1 to sdb1 . . . I kinda had to guess what it was, but it worked!  so any way, I had to go into /etc/fstab and change my device that was sdb1 to sdc1, and that works fine now, and also had to change the linux swap drive to sdb5 to get that working.  Well, read that page and you'll find out the rest.  good luck :KS

---

### Post by themole22 on 2006-03-14
I did actually find a solution to this one - if you are using a HPT374 (Highpoint Rocket 1540) the built-in drivers will not work, and the manufacturer supplied drivers do not compile under the 2.6 kernel. 

Oddly, the problem doesn't show up until you actually add a drive to the card. 

I have since swapped (with some sadness, as Ubuntu is far easier to use) to Slackware as its still based on 2.4 and everything is working (nearly!).

---

