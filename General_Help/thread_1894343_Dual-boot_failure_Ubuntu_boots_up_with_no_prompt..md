---
title: "Dual-boot failure: Ubuntu boots up with no prompt."
date: 2011-12-12
forum: General Help
---

### Post by Areze on 2011-12-12
Well, I tried installing Ubuntu 11.10 on my mother's computer in a hard drive format, and it does not work. It simply boots up Ubuntu with no options for windows.

The files are still there, just inaccessible.

When I was installing Ubuntu, I tried using the Partition system. I got the partitions working, but the drop-down box I left unchecked, I was unsure to what it did. Oops.

Now, I have no idea on how to get Ubuntu off the computer and Windows 7 working. The System Restore did nothing, the F11 restore option is unresponsive, and it does not read the recovery disk. It simply boots Ubuntu with absolutely no options as to what I am allowed to do.

I tried reinstalling Ubuntu, with the drop-down (root path, I think) set to the partition that Ubuntu will be installed on. Nothing.

I tried a command line to call up the GRUB. No dice.

I've given up. Is there ANYTHING I can do to reset the computer to out-of-the-box settings, and to get rid of Ubuntu?

I ran the Windows 7 disk repair and it did nothing.

---

### Post by Mark Phelps on 2011-12-12
When you install Ubuntu to its own partition, you overwrite the MBR code so that it defaults to booting Ubuntu.  So, of course, you will NOT see a menu for other OSs.  This is how it is SUPPOSED to work!

To get a new menu, one containing entries for other OSs, open a terminal in Ubuntu and enter "sudo update-grub".  That will force a scan for other OSs.  When you watch it run, you should see something like "Windows 7 (Loader) on xxx".  That means it found Win7.

When you then reboot, you should get a GRUB menu, including an entry (or two) for Win7.

If this PC came with Win7 preloaded, you might see two entries -- and they're likely to be mislabeled.  Used whichever entry works.

---

### Post by Areze on 2011-12-12
Well, I did, and it said it detected the three Win7 partitions.

When I reboot, it goes automatically to the Ubuntu log-in screen, as usual. :(

I should mention, when Ubuntu is booting, a gray box appears saying: "Out of Scan Range".

This stays in place until the log-in screen appears.

---

### Post by Mark Phelps on 2011-12-12
> **Areze said:**
> Well, I did, and it said it detected the three Win7 partitions...

This is odd.  Open a terminal in Ubuntu, enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here.

---

### Post by Areze on 2011-12-12
> **Mark Phelps said:**
> This is odd.  Open a terminal in Ubuntu, enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here.

Is this is?
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   547081847   273437500    7  HPFS/NTFS/exFAT
/dev/sda3       547082238   604762111    28839937    5  Extended
/dev/sda4       604762112   625139711    10188800    7  HPFS/NTFS/exFAT
/dev/sda5       547082240   600834047    26875904   83  Linux
/dev/sda6       600836096   604762111     1963008   82  Linux swap / Solaris
mom@mom-AY026AA-ABA-CQ5300F:~$ 


---

### Post by Areze on 2011-12-12
Well, thanks for you help and patience in fixing the problem.


We (my and my mom) managed to cobble a solution and got Win7 working. So with that out of the way, I'll try tinkering with Ubuntu on one of the spares we have in a closet.

Thanks again. :)

---

### Post by Rubi1200 on 2011-12-12
If you found a solution, please mark this thread Solved using the Thread Tools near the top of the page.

If you need more help with anything, let us know and we will be happy to assist you.

---

