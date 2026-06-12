---
title: "Deleting &quot;SYSTEM RECOVERY&quot; Partition"
date: 2011-01-19
forum: General Help
---

### Post by hi_pplz_567 on 2011-01-19
I was planning on completely erasing every single partition on my computer before going through the process of triple booting on my computer and there were two partitions I came across that I had some questions about.

There was a "PQSERVICE" partition. Which was said by Acer to be a "hard disk image" of the recovery disk that they prompted me to burn when I first got the computer. I told her that I'd burn the disk already and that it was okay to delete that partition now, if I wanted to, so that's not a problem.

Then, there is a "SYSTEM RESERVED" partition. Which the woman told me contained important files such like my BIOS. I believe that she was mistaken because I've never run across a computer with the BIOS that was stored on the hard drive of the computer, but my friends said that I should get a third opinion from all of you on here.

If you believe that she was mistaken let me know because I'd like to hurry up and get this done, I've been preparing for this for 3 days now. Haha.
I'm also sorry if there was a better area I could have posted this. I must have overlooked it.

Thanks alot! :)

EDIT: I belive that it is just a partition created by Windows 7 for "important" files that Windows needs. Correct me if I'm wrong.

---

### Post by Quackers on 2011-01-19
I presume you are talking about Windows 7? 
Firstly the system reserved partition seems to be a Win 7 preference. It's a small partition (sometimes only 100MB) that stores some Win 7 boot files.
Secondly I would check that your recovery dvd's work before the time that you need them! I would also make a Windows repair cd. Go to Control Panel > Backup & Restore Centre and in the left pane click on "make a Windows recovery cd". Windows calls it a recovery cd, but everybody else calls it a repair cd. You may need this disc!
If you are intending to use the recovery dvd's to re-install Win 7, it will most likely want to use the whole disc. If it does, you are likely to be resizing or creating partitions after re-installation. Make sure you don't exceed the maximum of 4 primary partitions (an extended partition is a primary).
Have fun :-)

---

### Post by hi_pplz_567 on 2011-01-19
Yes, I was talking about Windows 7.
I'll start burning the other disk right away. Thanks!

---

### Post by Quackers on 2011-01-19
You're welcome.

---

### Post by Hack.The.Pow. on 2011-01-20
just a word of caution.  I just got an acer netbook and eventually killed windows 7 on it.

after some partitioning Windows 7 broke and would no longer boot.  I tried everything on the recovery discs and more and still couldn't get it to work.

So I simply decided to delete those two partitions(PQSERVICE and SYSTEM RESERVED) because they were not helping.  Even trying to restore to factory image was broken.  I however did back them up into images just in case.

So I was left with a broken windows 7 partition that I didn't wanna delete because then I essentially just threw away windows.  I tried putting the PQSERVICE partition back on the computer but it won't even boot from it now.  

Now I'm left trying to compile a system image from like 150 files in the PQSERVICE partition to get windows back.

Just a caution when partitioning.  Try not to move around the Windows partitions.  Then are very finicky

Edit:  Be careful when using the factory image recovery!  One time even booting into that partition simply deleted my entire ubuntu partition!!

Also I love your avatar

---

### Post by fasoulas on 2011-01-31
> **Quackers said:**
> I presume you are talking about Windows 7? 
Firstly the system reserved partition seems to be a Win 7 preference. It's a small partition (sometimes only 100MB) that stores some Win 7 boot files.
Secondly I would check that your recovery dvd's work before the time that you need them! I would also make a Windows repair cd. Go to Control Panel > Backup & Restore Centre and in the left pane click on "make a Windows recovery cd". Windows calls it a recovery cd, but everybody else calls it a repair cd. You may need this disc!
If you are intending to use the recovery dvd's to re-install Win 7, it will most likely want to use the whole disc. If it does, you are likely to be resizing or creating partitions after re-installation. Make sure you don't exceed the maximum of 4 primary partitions (an extended partition is a primary).
Have fun :-)

That small partition you mentioned ,do you know exactly what it does and if it is really necessary.
Can i delete it?
I am asking because i have a hard disk on a sony vaio e series and it has 3 partitions ,windows,system-reserved(100MB) and a recovery partition and i was wondering how can i install ubuntu on it because of the 4 partitions limit.

---

### Post by Jouke74 on 2011-01-31
You can always burn the Clonezilla ISO make an image of the whole harddisk and store it on the external drive for the time being. After you have run Ubuntu for a month and notice things don't go wrong you can delete it if you want. At least you have a backup before deleting important stuff, which can easily be restored.

Also on my Asus EEE there is a small EFI boot partition which actually does contain the BIOS. If you enable boot booster in the BIOS this partition is read instead of waiting for the full BIOS checks to be run. It saves the BIOS startup screen plus all waiting for the hardware to be checked. Instead it starts straight with the OS. So first check your manual for these things...

---

### Post by fasoulas on 2011-01-31
> **Jouke74 said:**
> You can always burn the Clonezilla ISO make an image of the whole harddisk and store it on the external drive for the time being. After you have run Ubuntu for a month and notice things don't go wrong you can delete it if you want. At least you have a backup before deleting important stuff, which can easily be restored.

Also on my Asus EEE there is a small EFI boot partition which actually does contain the BIOS. If you enable bot booster in the BIOS this partition is read instead of waiting for the full BIOS checks to be run. It saves the BIOS startup screen plus all waiting for the hardware to be checked. Instead it starts straight with the OS. So first check your manual for these things...

thanks for the answer
I think that mine also has something to do with EFI boot because i just mounted it using ntfs-3g(am on the live cd) and it has files like bootmgr.exe.mui and memtest.exe.mui .

So. what happens if i delete this partition???

---

### Post by Jouke74 on 2011-01-31
PQSERVICE partition is the Windows recovery tool from ACER. Basically the complete image from Windows7 + Drivers + Programs which you installed when you booted the laptop the first time.

SYSTEM RESERVED is the boot recovery partition from Windows 7. In case something bad happened to the boot or system files, Windows 7 can use this one to fix the MBR etc. 

If you want to restore Windows later I suggest you keep PQSERVICE. If you are sure you never want to install Windows 7 again you can erase both partitions. It might be hard(er) later to get a working Windows 7 on this computer again.

---

