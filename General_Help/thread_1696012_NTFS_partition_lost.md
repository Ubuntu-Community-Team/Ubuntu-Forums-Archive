---
title: "NTFS partition lost"
date: 2011-02-26
forum: General Help
---

### Post by sauronnikko on 2011-02-26
Hello. I'm using Windows 7 and Ubuntu in two differents partitions in my hard drive. I was on Windows 7 and decided to reboot. When the grub screen should have appeared, instead the computer rebooted itself. It continues to do so. I put Ubuntu 10.10 Live CD and it keeps "loading" forever, but doesn't hang. In the console, it said something like "input/output" error. I tried with my Win 7 DVD and it was the same: it doesn't reach the part where it shows the menu with all the installation options.

I tried with Gparted and it loaded fine. It showed all my partitions, but there wasn't (I think) more that I could have done with it. I tried then user Super Grub Boot. I finally could enter Ubuntu. Everything is fine except that it doesn't show my Window partition. It's like it doesn't exist anymore, so I can't backup my files. Now, I haven't tried loading Win 7 from Super Grub Boot (I'm going to do it just as soon as I post this), but this is pretty weird. Anyone have any idea what is going on and what can I do to this this? Thanks!

---

### Post by sauronnikko on 2011-02-26
Ok, from Super Grub I can get to Win 7. But the problem persists: when booting from the Hard Drive without any help from Super Grub, the PC reboots, and, in Ubuntu, I can't access my Windows partition. The boot sector must be messed up, but I've got no idea of how to repair it (as I said in the previous post, Ubuntu Live CD is not working either)

---

### Post by seawolf167 on 2011-02-26
See if [this link]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") on reinstalling GRUB2 helps you.

As always, I suggest making backups before you do anything. [Clonezilla]("http://www.clonezilla.org/") is my backup program of choice

---

### Post by Mark Phelps on 2011-02-26
Before you installed Ubuntu, you should have used the Backup feature in Win7 to create and burn a Win7 Repair CD.  If you had that now, you could use it to repair your Win7 boot loader.

Since you didn't do that, go to the link below and download the proper Win7 repair CD image:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Burn that to CD.  Boot from the CD and run Startup Repair.  You may have to run it three times to fix everything.

---

### Post by samacaster on 2011-02-26
You can use the SuperGrub CD to get back into Ubuntu? Once into Ubuntu open your terminal and type: sudo update-grub 

your output should be something like:

Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows7(loader) Dev/sda1

However, if you've lost your BCD/MBR for windows grub won't "find" it. You'll have to get the start-up repair disc mention earlier in this thread. But instead of using the start-up repair function, which can take up to 4 times to work, do this.

Choose the command prompt. When the command prompt opens type C:

then: bootrec.exe /fixmbr  This places a generic win7 MBR onto the drive

then: bootrec.exe /rebuildbcd  This completely rebuilds the entire boot sector

Once you can get windows up and running you'll have to stick in the LiveCD for Ubuntu and restore grub using the excellent instructions on the link from an earlier reply.

---

### Post by sauronnikko on 2011-02-26
I did an update-grub but it didn't work. To do bootrec, I'd need to be able to use the console from the Windows 7 DVD, but remember that no menu appears, it just shows the background and stops loading. With Ubuntu Live CD is almost the same. The Ubuntu logo is shown and beneath it, the dots act as it if was loading, but it never does. It just stays there. 

I remember some years ago I had some issue with GRUB, in which it didn't load but at least it gave me an error message. Now, the system is rebooted before anything from GRUB appears.

I think the problem has to be serious if Ubuntu Live CD and Win 7 installation discs can't do anything, but I don't know.

---

