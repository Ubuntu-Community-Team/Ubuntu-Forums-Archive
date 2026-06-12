---
title: "Would Windows System Recovery remove Ubuntu?"
date: 2010-02-08
forum: General Help
---

### Post by daphnestory on 2010-02-08
I have my reasons for doing a Windows system recovery, and no doing a Linux recovery would not help. Okay, so I installed Linux 9.10 Karmic from the Live CD I got in the mail, and I now have it dual booting with Windows XP (XP installed first). I'm using HP Pavilion a320n with AMD Athalon XP Processer, preinstalled with XP, no installation or recovery disk.

I realized that I can navigate through everything from the C:/ drive to the desktop of my XP partition by mounting "HP_PAVILION" (obviously the hard drive) in the Places tab from within Ubuntu. I also think the built-in Win recovery must be on a separate partition because it shows as a seperate option in the GRUB menu. Because, when I boot windows from the GRUB it doesn't show the separate screen that prompted me to press F1 for recovery before reaching the splash screen like it used to, and I also remember drive D:/ being a drive in the My Computer folder next to C:/, saying that I wasn't allowed to browse the folder because it was for recovery purposes. I also realized that I could navigate my Ubuntu desktop and filesystem by going to the Ubuntu folder in my C:/ drive from within the windows partition. So now for the main question:

I want to know if doing the system recovery that came preinstalled on the machine  will delete the ubuntu partition and all files on it (because I was also working on a very important project within XP and was planning on copying and pasting the files from within Linux in order to back them up onto my linux partition, because I can't by an external hd and they're too much for a flash drive).

 Will Windows system recovery delete Linux, and afterwards will I be able to boot normally into windows without any boot problems, like will it automatically configure the MBR? Or will is just replace the GRUB bootloader with the Windows MBR, and all I would have to do is use the Live CD to restore the GRUB menu. Because the main thing I need is XP, so I'd just reinstall Linux if it got deleted, but the thing is, I wanted to back up my desktop files onto my linux partition and restore them later. With Windows System recovery actually formate the ENTIRE hard disk or just the Windows partition on the hard disk, meaning I'd be able to simply pop in the Live CD, fix the GRUB menu, and Ubuntu Karmic will be back with all the files I backed up from my windows partition? Or will everything just be completely replace with Windows? Btw, I do believe I resized the Windows partition to about 20 Gigs smaller than originally when I installed linux, so will this cause the system recovery to resize the partition itself, thus overwriting Linux, especially since I believe the sys recov has it's very own partition separate from the actual windows partition.

---

### Post by umoreno_89 on 2010-02-08
answer: no

system recovery, i think you mean "restore", will remove any edits that has occurred on the Windows partition, not the whole hard drive.

---

### Post by JKyleOKC on 2010-02-08
In most systems, the Windows Recovery Partition will wipe out the entire hard disk and put the machine back to factory condition. The only way to preserve your project would be to copy it to an external drive and then disconnect that external drive while doing the recovery.

Note, too, that any special software you may have installed will also be wiped out and will have to be re-installed.

These recovery partitions actually just have a compressed disk image of the factory setup, and automatically replace the entire content of the drive with the uncompressed image.

---

