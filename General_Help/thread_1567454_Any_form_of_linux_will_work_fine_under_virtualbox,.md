---
title: "Any form of linux will work fine under virtualbox, but not if actually installed"
date: 2010-09-03
forum: General Help
---

### Post by Donzieja on 2010-09-03
Every time I try to install Linux on my computers HDD it will eventually start to boot/install, but even getting to the screen with the loading "dots" takes about 15 minutes, and about 45 minutes to get through that screen, followed by another hour and a half of some codes which always seem to end in "EH Complete." Either that or "EH ok". I can't remember. Anyways, this problem started after getting the computer back from repairs, and I have posted this before, but now I have more knowledge of what I'm posting so hopefully we can work something out this time.

Thanks in advance, 

-Don

---

### Post by tyblogger5 on 2010-09-03
Hmm...that is weird, what repairs exactly did you have?

---

### Post by blazemore on 2010-09-03
Sounds like it might be an issue with the way the hard disk is configured in the BIOS.
If your hard disk is connected with a SATA cable, and your BIOS has an option for it, try changing from IDE emulation to AHCI, or vice versa.

This fixed a similar problem I was having, where I couldn't boot from my CD-rom drive.

---

### Post by Donzieja on 2010-09-03
I got the motherboard replaced due to a faulty power jack, and the thing that covers the cd tray... and also the audio out port.

---

### Post by blazemore on 2010-09-04
> **Donzieja said:**
> I got the motherboard replaced due to a faulty power jack

New motherboard = new BIOS.

You had to re-install Windows, right?

It's worth going through your BIOS settings and disabling devices you don't use. For example, if you don't physically have a floppy drive in your computer, change the Floppy option in the BIOS from "Auto" to "Off". The same applies to any hard disks you don't use (I have 1 hard disk, so I disabled my other SATA ports - they don't get checked at boot)

This will "clear the desk" and help prevent any conflicts. It will also have the additional benefit of making your PC boot at least 3 or 4 seconds faster.

Did you try the AHCI tweak? Let me know how that goes.

---

### Post by tyblogger5 on 2010-09-04
I think that blazemore will be able to help you more than I.  I haven't worked on any hardware problems before.

---

### Post by Donzieja on 2010-09-04
It came with vista, so I installed 7.

-EDIT-

I also heard that booting with "irqfixup" would help.

---

### Post by Donzieja on 2010-09-05
okay. It is set to AHCI mode, so i dont know whats up really. everything seems to be regular. i just cant find the problem. how would I add Irqfixup to the boot options? i heard it was to be placed between RO and quiet but i cant find those anywhere in the boot options, well, not next to each other anyways.

Help?

-Don

---

### Post by blazemore on 2010-09-05
> **Donzieja said:**
> okay. It is set to AHCI mode, so i dont know whats up really. everything seems to be regular. i just cant find the problem. how would I add Irqfixup to the boot options? i heard it was to be placed between RO and quiet but i cant find those anywhere in the boot options, well, not next to each other anyways.

Help?

-Don

The order doesn't matter. Stick it anywhere. Try doing it on a 1-off basis before you edit /etc/grub/default though.

---

### Post by Donzieja on 2010-09-05
okay. thanks. will do.

---

### Post by Donzieja on 2010-09-05
It didn't work. :(

---

### Post by Donzieja on 2010-09-16
Bump. Still nothing... Anyone have any ideas out there?

---

### Post by wilee-nilee on 2010-09-17
> **Donzieja said:**
> Bump. Still nothing... Anyone have any ideas out there?


So how much memory are you allocating. I use about 750mib for maverick, and I set the display in settings to 128mib.

What distro is it?

---

### Post by Donzieja on 2010-09-17
I'm talking about actually installing it, therefore allocating it the full amount of both memory and video memory.

---

### Post by Donzieja on 2010-09-19
It's been happening on all distros. Most recent? 9.10 lucid lynx amd 64... yes i have amd 64.

---

