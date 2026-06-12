---
title: "Grub2 kills my win7 boatloader"
date: 2010-08-25
forum: General Help
---

### Post by elliotn on 2010-08-25
Every time I boot into ubuntu, later on when I boot into Windows 7 the Startup is messed and I have to repair startup always.

2nd. My grub shows 2 win7, 2 unknow linux distributions(puppy 5) and ubuntu.
 
Anyone knows why?

---

### Post by wilee-nilee on 2010-08-25
Who was the computer manufacturer?

---

### Post by elliotn on 2010-08-25
> **wilee-nilee said:**
> Who was the computer manufacturer?

What I dont get u

---

### Post by dwel on 2010-08-25
> **elliotn said:**
> What I dont get u

I think they are asking you: "What brand name is your computer?" Dell, HP, Toshiba.........

---

### Post by elliotn on 2010-08-25
> **dwel said:**
> I think they are asking you: "What brand name is your computer?" Dell, HP, Toshiba.........

There is a summary of my PC in my sig

---

### Post by burton247 on 2010-08-25
Did you build it yourself or buy it?

---

### Post by elliotn on 2010-08-25
I made it myself, but whatz that gotta do with the grub2 messing up windows bootloader, if I only use Windows the issue doesnt happen, the same machine worked well with grub legacy in 9.04 and 9.10 dual booting with windows

---

### Post by wilee-nilee on 2010-08-25
> **elliotn said:**
> I made it myself, but whatz that gotta do with the grub2 messing up windows bootloader, if I only use Windows the issue doesnt happen, the same machine worked well with grub legacy in 9.04 and 9.10 dual booting with windows

As another poster mentioned Dell and HP have programs that will mess up the bootloader. Your running W7 with 512mb of ram, in order to do this you would have to have tweaked W7 a lot.

Post the bootscript in my signature in code tags as described.

---

### Post by Mark Phelps on 2010-08-25
What I've read is that some vendors install SW on their machines that "protect" the MBR against rootkits, such that, if you mess with the MBR (which you would when you install GRUB/GRUB2 to it), the machine either refuses to boot, or boots into a mode that forces the restoration of the original MBR code.

Sorry, but I know of no way to disable this "feature".

---

### Post by elliotn on 2010-08-25
> **Mark Phelps said:**
> What I've read is that some vendors install SW on their machines that "protect" the MBR against rootkits, such that, if you mess with the MBR (which you would when you install GRUB/GRUB2 to it), the machine either refuses to boot, or boots into a mode that forces the restoration of the original MBR code.

Sorry, but I know of no way to disable this "feature".

I previously had success when it comes with dual booting with grub legacy, and I run win7 with 1Gb ram + a 512mb ram not 512mb

---

### Post by oldfred on 2010-08-25
Are you hibernating windows and then in Ubuntu adding or moving files in the windows partition? That corrupts the hibernation in most cases.

---

### Post by varunendra on 2010-08-27
The Boot Info Script may help narrow down speculations, so why don't you post its output as wilee-nilee asked! If it couldn't help, it won't hurt either! ;)

---

