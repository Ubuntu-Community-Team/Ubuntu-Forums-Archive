---
title: "Removing Ubuntu"
date: 2006-05-30
forum: General Help
---

### Post by Zdravko on 2006-05-30
If I want to remove completely Ubuntu from my computer, what steps should I follow? I am currently with dual-boot - Windows XP. Of course Windows should remain as OS.


P.S. Don't get me wrong - I still adore Ubuntu. I only wish to make a clean and fresh installation for Dapper.

---

### Post by ifokkema on 2006-05-30
[QUOTE=Zdravko]I only wish to make a clean and fresh installation for Dapper.[/QUOTE]

In that case, I would just throw in the Dapper install CD and have it format the linux partition that you select as the install partition. Breezy had that option, so I assume that Dapper does, too.

HTH,

Ivo

---

### Post by Zdravko on 2006-05-30
[ifokkema]("http://ubuntuforums.org/member.php?u=114075"), hm ok. But I am afraid, that the GRUB manager will break down?

---

### Post by Fillado on 2006-05-30
This is how I do it if I ever need to (might be a bit long winded but it never fails :) ):

Boot from your Windows CD
Go into the recovery console (there isn't a password set for administrator by default so just hit enter).
Make sure you're at the C prompt (C:\> or something like that) (usually just typing "cd .." and hitting enter will get your there)
Type "fixmbr" and follow it through
Reboot and you should go straight into Windows with no GRUB

Download [SystemRescueCD]("http://www.sysresccd.org/")
Boot it up from a CD and follow it through into qt_parted
Then just delete all your Linux partitions, resize your Windows one to the maximum, and commit the changes.

And there you go, a system completely de-Ubuntu'd :)

---

### Post by ifokkema on 2006-05-30
[QUOTE=Zdravko][ifokkema]("http://ubuntuforums.org/member.php?u=114075"), hm ok. But I am afraid, that the GRUB manager will break down?[/QUOTE]

Hi,

No, well, if grub is already there, nothing will change since after the install, Dapper will have a /boot/grub/menu.lst as well. If you have your Windows boot loader, during installation of dapper you can select if Dapper will install grub in the MBR.

@Fillado: He doesn't want to get rid of Linux, he wants a fresh start with Dapper.

Ivo

---

### Post by Zdravko on 2006-05-30
Ok, just to clear things now, because I am a little confused:
1. Dapper CD inserted.
2. Formatting Breeze partition
3. Installing Dapper.
These steps will lead to overwriting the previous GRUB with the Dapper's GRUB? And I will be able again to select between Windows and Ubuntu Dapper?

---

### Post by ifokkema on 2006-05-31
[QUOTE=Zdravko]Ok, just to clear things now, because I am a little confused:
1. Dapper CD inserted.
2. Formatting Breeze partition
3. Installing Dapper.
These steps will lead to overwriting the previous GRUB with the Dapper's GRUB? And I will be able again to select between Windows and Ubuntu Dapper?[/QUOTE]

1) Insert Dapper CD and start install process.
2) You will be asked where Dapper should be installed. Just choose your current Linux root partition, and select it to be formatted (should be the default choice).
3) It will also ask you if you want to install Grub in the MBR. Just select it to be installed, and everything will be just fine. It will detect other operating systems on your computer, including Windows.

Ivo

---

