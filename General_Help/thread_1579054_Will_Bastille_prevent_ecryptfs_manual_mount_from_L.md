---
title: "Will Bastille prevent ecryptfs manual mount from LiveCD?"
date: 2010-09-21
forum: General Help
---

### Post by in.flex.ion on 2010-09-21
Hi everyone, i m new here. And i need help :( I have been googlin since Sun, and this is beyond me. I have been using Ubuntu <6mths. Here goes :

1. I was just given a fairly-new netbook with UNR 10.04. Dual boot with XP Home. Bastille hardened. Encrypted home folder. I have my boss's login pass. Gave it the latest updates over the wkend. Rebooted.

2. On reboot, i noticed a Grub entry - Vista something - and i got itchy, so i tried it. And that was how my woes began. 

Error : file not found
grub rescue >

(i have not told her i didnt backup her data ](*,))

3. Here's the catch. Unlike the other google results, i dont see Linux or Linux/Solaris swap when i sudo fdisk -l (below). I believe UNR is in /dev/sda3 but it says Extended :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3113a989

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  12  Compaq diagnostics
/dev/sda2   *         915       12731    94919677+   7  HPFS/NTFS
/dev/sda3           12732       19457    54026593+   5  Extended
/dev/sda5           18152       19457    10490413+   7  HPFS/NTFS

4.  LiveCd only sees sda2 (WinXP). i dont know why sda1 = compaq diagnostics when the netbook is an acer.

5. But when i sudo mount /dev/sda1 /mnt - error message returned "mount: you must specify the file system type". So i can't do Dustin's blog - [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html).  

6. i also tried SuperGrub2 and Rescatux (unless i didnt use them right). 

7. FYI, at grub rescue, "ls" reports (hd0) (hd0,5) (hd0,2) (hd0,1). i cannot seem to get other commands going.

8. I thought it might be Bastille, so i installed it on a Ubuntu desktop with encrypted home folder, but i cant repeat the above with LiveCD. I dont know enough if its Bastille or not.

9. Do i do a sudo mount -t ecryptfs? But if i dont have the mount passphrase, only the login?

10. Its ok that i cant get UNR back as long as i can access home folder and copy out what's inside.

:confused: Thanks, much appreciate any pointers. Cheers

---

### Post by in.flex.ion on 2010-09-22
hi, can any1 help? I attached results from bootinfoscript - will any1 help me interprete it?

1. i am goin to try access the WinXP (/dev/sda2) by fixing mbr. at least, i get that os goin.

rgds

---

