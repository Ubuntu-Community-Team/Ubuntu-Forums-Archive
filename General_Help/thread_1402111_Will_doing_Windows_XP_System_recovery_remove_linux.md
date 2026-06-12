---
title: "Will doing Windows XP System recovery remove linux?"
date: 2010-02-08
forum: General Help
---

### Post by daphnestory on 2010-02-08
Okay, so I installed Linux 9.10 Karmic from the Live CD I got in the mail, and I now have it dual booting with Windows XP (XP installed first). On the GRUB menu it shows Ubuntu 9.10 generic, ubuntu 9.10 recovery console, two options say say something about "mem test", windows 98, 2000, XP, and then Windows XP home edition. In that order. now, I got a virus on XP that can only be removed by system recovery (trust me, I've tried there's no other way). Now, I noticed that the option saying Win 98, 2K, XP is actually the built in recovery mode that restores to factory defaults (I'm using HP Pavilion a320n with AMD Athalon XP Processer, preinstalled with XP, no installation or recovery disk).

I realized that I can navigate through everything from the C:/ drive to the desktop of my XP partition by mounting "HP_PAVILION" (obviously the hard drive) in the Places tab from within Ubuntu. I also think the built-in Win recovery must be on a separate partition,otherwise it wouldn't be seperate in the GRUB menu, right? Because, when I boot windows from the GRUB it doesn't show the separate screen that prompted me to press F1 for recovery before reaching the splash screen like it used to, and I also remember drive D:/ being a drive in the My Computer folder next to C:/, saying that I wasn't allowed to browse the folder because it was for recovery purposes. I also realized that I could navigate my Ubuntu desktop and filesystem by going to the Ubuntu folder in my C:/ drive from within the windows partition. So now for the main question:

If I choose the system recovery option, it says I can either choose to delete any updates and installed programs and restore to factory defaults, however it will keep all data files created since then, or I can choose what it calls the "destructive system recovery" with deletes any and all post-purchase installed programs, updates AND data files. I want to know if doing the system recovery preinstalled by windows XP will delete the ubuntu partition and all files on it (because I was also working on a very important project within XP and was planning on copying and pasting the files from within Linux in order to back them up onto my linux partition, because I can't by an external hd and they're too much for a flash drive).

 Will Windows system recovery delete Linux, and afterwards will I be able to boot normally into windows, like will it automatically configure the MBR? Or will is just replacethe GRUB bootloader with the Windows MBR, and all I would have to do is use the Live CD to restore the GRUB menu. Because the main thing I need is XP, so I'd just reinstall Linux if it got deleted, but the thing is, I wanted to back up the files on my windows desktop onto my linux partition and restore them later. Will Windows System recovery actually format the ENTIRE hard disk or just the Windows partition on the hard disk, meaning I'd be able to simply pop in the Live CD, fix the GRUB menu, and Ubuntu Karmic will be back with all the files I backed up from my windows partition? Or will everything just be completely replace with Windows? Btw, I do believe I resized the Windows partition to about 20 Gigs smaller than originally when I installed linux, so will this cause the system recovery to resize the partition itself, thus overwriting Linux, especially since I believe the sys recov has it's very own partition separate from the actual windows partition.

---

### Post by aaaantoine on 2010-02-09
If it's a recovery partition, there's a strong chance that it will try to restore the drive to its original partition(s).  I'd recommend backing up your Windows documents *and* your /home folder to an external storage device.

Whatever it does, if it succeeds you will at the very least have to reload GRUB into the MBR.

(I really wish these manufacturers would give you a disk like they used to.)

---

### Post by john newbuntu on 2010-02-09
Since you resized the windows partition (less 20GB), I doubt if recovery will proceed normally since the recovery tool generally verifies that the partition table is as expected before proceeding (at least that is what Dell system recovery tool does). I have a Dell and I am not competent enough to answer this question on HP.   It sounds like you have a WUBI install since you can access Ubuntu partitions from within windows.  Is that correct?

Would compressing your data files(using gzip) and storing it on a flash drive help?  Because should the restore utility decide to carve away the Ubuntu partition, you would lose it.  Anyway, please wait for someone who has done this in HP/Compaq to get a second opinion.  Also, please post this on the HP forums to see what you can glean.

---

### Post by NightwishFan on 2010-02-10
I have recovered Dell and Compaq systems that reinstall and keep Linux. You will need to reinstall GRUB as was said above.

---

### Post by Mark Phelps on 2010-02-10
I have recovered HP systems and in all cases, the hard drive was completely erased and reformatted.  That's not so say that YOUR recovery will work the same -- but it's more likely to do that instead of what Dell or Compaq do.

Either way, as others have suggested, you will need to back off and save any data before you do a restore.

---

