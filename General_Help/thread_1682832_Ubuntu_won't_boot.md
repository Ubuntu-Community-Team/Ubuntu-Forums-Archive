---
title: "Ubuntu won't boot"
date: 2011-02-06
forum: General Help
---

### Post by JBA2337 on 2011-02-06
On my computer I have Windows XP SP3 (partition sda1) and Ubuntu 10.04 (partition sda2). For some reason my computer system won't start up at all.

Whenever I restart the computer I get this message:

 [B]error: file not found

 grub rescue>
[/B]

I tried to fix grub by booting a Super Grub disk (v 0.9799). I selected **Gnu/Linux >  Fix Boot of Gnu/Linux (GRUB)** and that did not work.  I got an error message that said:
[B]Error 15: File not found
   Booting 'not lucky'
pause SGD has NOT succeeded :(
SGD has NOT succeeded :(
[/B]
I then tried to fix grub by booting a Rescatux disk (v 0.22). I selected **GRUB options > Restore Grub > Run**.  This program could not access the sda2 partition, so that did not work. 

All my attempts to restore GRUB failed.

I then booted my computer from an Ubuntu Live CD disk, and I tried to mount the Ubuntu partition manually, using the terminal command **sudo mount /dev/sda2 /mnt**, but it would not mount.  I got the following error:

 [B]mount:  wrong fs type, bad option, bad superblock on /dev/sdb1,

 missing codepage or helper program, or other error

 In some cases useful info is found in syslog - try

 dmesg | tail or so[/B]

Finally I  tried to repair the Ubuntu partition, so I ran 
**sudo e2fsck -f -y -v /dev/sda2**. This did not work. It ended with "e2fsck aborted". Here are the complete details:


```
[B]sudo e2fsck -f -y -v /dev/sda2

e2fsck: Group descriptors look bad... trying backup blocks...

Resize inode not valid. Recreate? yes


Pass 1: Checking inodes, blocks, and sizes

Group 0's inode table at 15 conflicts with some other fs block.

Relocate? yes



Group 0's block bitmap at 13 conflicts with some other fs block.

Relocate? yes



Group 0's inode bitmap at 14 conflicts with some other fs block.

Relocate? yes



Group 1's inode table at 32783 conflicts with some other fs block.

Relocate? yes



Group 1's block bitmap at 32781 conflicts with some other fs block.

Relocate? yes



Group 1's inode bitmap at 32782 conflicts with some other fs block.

Relocate? yes



Group 3's inode table at 98319 conflicts with some other fs block.

Relocate? yes



Group 3's block bitmap at 98317 conflicts with some other fs block.

Relocate? yes



Group 3's inode bitmap at 98318 conflicts with some other fs block.

Relocate? yes



Group 5's inode table at 163855 conflicts with some other fs block.

Relocate? yes



Group 5's block bitmap at 163853 conflicts with some other fs block.

Relocate? yes



Group 5's inode bitmap at 163854 conflicts with some other fs block.

Relocate? yes



Group 7's inode table at 229391 conflicts with some other fs block.

Relocate? yes



Group 7's block bitmap at 229389 conflicts with some other fs block.

Relocate? yes



Group 7's inode bitmap at 229390 conflicts with some other fs block.

Relocate? yes



Group 9's inode table at 294927 conflicts with some other fs block.

Relocate? yes



Group 9's block bitmap at 294925 conflicts with some other fs block.

Relocate? yes



Group 9's inode bitmap at 294926 conflicts with some other fs block.

Relocate? yes



Group 25's inode table at 819215 conflicts with some other fs block.

Relocate? yes



Group 25's block bitmap at 819213 conflicts with some other fs block.

Relocate? yes



Group 25's inode bitmap at 819214 conflicts with some other fs block.

Relocate? yes



Group 27's inode table at 884751 conflicts with some other fs block.

Relocate? yes



Group 27's block bitmap at 884749 conflicts with some other fs block.

Relocate? yes



Group 27's inode bitmap at 884750 conflicts with some other fs block.

Relocate? yes



Group 49's inode table at 1605647 conflicts with some other fs block.

Relocate? yes



Group 49's block bitmap at 1605645 conflicts with some other fs block.

Relocate? yes



Group 49's inode bitmap at 1605646 conflicts with some other fs block.

Relocate? yes



Group 81's inode table at 2654223 conflicts with some other fs block.

Relocate? yes



Group 81's block bitmap at 2654221 conflicts with some other fs block.

Relocate? yes



Group 81's inode bitmap at 2654222 conflicts with some other fs block.

Relocate? yes



Group 125's inode table at 4096015 conflicts with some other fs block.

Relocate? yes



Group 125's block bitmap at 4096013 conflicts with some other fs block.

Relocate? yes



Group 125's inode bitmap at 4096014 conflicts with some other fs block.

Relocate? yes



Group 243's inode table at 7962639 conflicts with some other fs block.

Relocate? yes



Group 243's block bitmap at 7962637 conflicts with some other fs block.

Relocate? yes



Group 243's inode bitmap at 7962638 conflicts with some other fs block.

Relocate? yes



Group 343's inode table at 11239439 conflicts with some other fs block.

Relocate? yes



Group 343's block bitmap at 11239437 conflicts with some other fs block.

Relocate? yes



Group 343's inode bitmap at 11239438 conflicts with some other fs block.

Relocate? yes



Group 625's inode table at 20480015 conflicts with some other fs block.

Relocate? yes



Group 625's block bitmap at 20480013 conflicts with some other fs block.

Relocate? yes



Group 625's inode bitmap at 20480014 conflicts with some other fs block.

Relocate? yes



Group 729's inode table at 23887887 conflicts with some other fs block.

Relocate? yes



Group 729's block bitmap at 23887885 conflicts with some other fs block.

Relocate? yes



Group 729's inode bitmap at 23887886 conflicts with some other fs block.

Relocate? yes



Inode 1 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Root inode is not a directory. Clear? yes



Inode 8, i_blocks is 0, should be 262408. Fix? yes



Inode 17 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 33 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 49 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 65 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 81 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 97 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 113 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 129 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 145 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 161 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 177 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 193 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 209 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 225 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 241 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 257 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 273 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 289 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 305 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 321 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 337 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 353 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 369 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 385 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 401 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 417 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 433 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 449 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 465 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 481 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 497 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 513 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 529 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 545 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 561 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 577 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 593 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 609 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 625 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 641 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 657 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 673 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 689 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 705 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 721 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 737 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 753 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 769 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 785 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 801 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 817 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 833 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 849 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 865 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 881 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 897 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 913 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 929 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 945 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 961 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 977 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 993 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1009 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1025 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1041 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1057 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1073 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1089 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1105 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1121 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1137 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1153 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1169 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1185 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1201 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1217 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1233 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1249 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1265 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1281 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1297 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1313 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1329 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1345 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1361 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1377 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1393 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1409 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1425 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1441 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1457 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1473 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1489 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1505 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1521 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1537 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1553 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1569 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1585 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1601 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1617 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1633 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1649 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1665 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1681 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1697 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1713 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1729 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1745 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1761 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1777 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1793 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1809 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1825 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1841 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1857 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1873 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1889 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1905 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1921 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1937 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1953 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1969 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 1985 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2001 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2017 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2033 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2049 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2065 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2081 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2097 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2113 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2129 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2145 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2161 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2177 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2193 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2209 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2225 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2241 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2257 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2273 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2289 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2305 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2321 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2337 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2353 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2369 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2385 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2401 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2417 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2433 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2449 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2465 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2481 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2497 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2513 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2529 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2545 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2561 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2577 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2593 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2609 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2625 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2641 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2657 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2673 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2689 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2705 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2721 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2737 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2753 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2769 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2785 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2801 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2817 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2833 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2849 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2865 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2881 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2897 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2913 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2929 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2945 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2961 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2977 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 2993 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3009 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3025 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3041 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3057 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3073 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3089 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3105 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3121 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3137 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3153 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3169 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3185 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3201 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3217 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3233 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3249 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3265 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3281 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3297 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3313 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3329 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3345 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3361 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3377 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3393 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3409 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3425 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3441 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3457 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3473 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3489 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3505 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3521 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3537 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3553 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3569 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3585 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3601 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3617 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3633 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3649 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3665 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3681 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3697 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3713 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3729 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3745 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3761 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3777 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3793 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3809 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3825 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3841 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3857 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3873 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3889 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3905 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3921 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3937 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3953 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3969 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 3985 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4001 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4017 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4033 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4049 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4065 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4081 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4097 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4113 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4129 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4145 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4161 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4177 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4193 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4209 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4225 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4241 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4257 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4273 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4289 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4305 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4321 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4337 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4353 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4369 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4385 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4401 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4417 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4433 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4449 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4465 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4481 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4497 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4513 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4529 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4545 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4561 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4577 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4593 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4609 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4625 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4641 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4657 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4673 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4689 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4705 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4721 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4737 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4753 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4769 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4785 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4801 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4817 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4833 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4849 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4865 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4881 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4897 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4913 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4929 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4945 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4961 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4977 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 4993 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5009 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5025 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5041 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5057 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5073 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5089 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5105 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5121 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5137 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5153 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5169 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5185 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5201 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5217 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5233 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5249 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5265 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5281 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5297 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5313 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5329 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5345 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5361 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5377 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5393 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5409 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5425 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5441 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5457 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5473 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5489 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5505 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5521 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5537 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5553 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5569 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5585 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5601 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5617 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5633 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5649 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5665 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5681 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5697 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5713 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5729 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5745 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5761 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5777 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5793 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5809 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5825 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5841 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5857 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5873 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5889 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5905 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5921 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5937 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5953 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5969 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 5985 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6001 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6017 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6033 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6049 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6065 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6081 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6097 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6113 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6129 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6145 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6161 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6177 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6193 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6209 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6225 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6241 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6257 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6273 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6289 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6305 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6321 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6337 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6353 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6369 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6385 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6401 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6417 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6433 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6449 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6465 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6481 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6497 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6513 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6529 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6545 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6561 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6577 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6593 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6609 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6625 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6641 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6657 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6673 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6689 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6705 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6721 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6737 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6753 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6769 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6785 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6801 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6817 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6833 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6849 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6865 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6881 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6897 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6913 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6929 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6945 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6961 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6977 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 6993 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7009 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7025 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7041 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7057 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7073 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7089 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7105 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7121 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7137 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7153 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7169 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7185 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7201 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7217 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7233 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7249 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7265 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7281 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7297 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7313 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7329 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7345 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7361 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7377 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7393 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7409 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7425 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7441 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7457 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7473 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7489 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7505 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7521 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7537 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7553 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7569 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7585 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7601 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7617 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7633 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7649 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7665 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7681 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7697 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7713 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7729 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7745 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7761 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7777 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7793 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7809 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7825 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7841 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7857 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7873 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7889 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7905 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7921 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7937 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7953 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7969 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 7985 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8001 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8017 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8033 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8049 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8065 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8081 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8097 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8113 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8129 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8145 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8161 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 8177 has EXTENTS_FL flag set on filesystem without extents support.

Clear? yes



Inode 405966 has illegal block(s). Clear? yes



Illegal block #17 (1297014482) in inode 405966. CLEARED.

Inode 407104 has illegal block(s). Clear? yes



Illegal block #17 (1297014482) in inode 407104. CLEARED.

Inode 407190 has illegal block(s). Clear? yes



Illegal block #17 (1297014482) in inode 407190. CLEARED.

Relocating group 0's block bitmap from 13 to 1032...

Relocating group 0's inode bitmap from 14 to 1033...

Relocating group 0's inode table from 15 to 1820...

Relocating group 1's block bitmap from 32781 to 33810...

Relocating group 1's inode bitmap from 32782 to 33811...

Relocating group 1's inode table from 32783 to 33812...

Relocating group 3's block bitmap from 98317 to 99336...

Relocating group 3's inode bitmap from 98318 to 99337...

Error allocating 512 contiguous block(s) in block group 3 for inode table: Could not allocate block in ext2 filesystem

Relocating group 5's block bitmap from 163853 to 164872...

Relocating group 5's inode bitmap from 163854 to 164873...

Error allocating 512 contiguous block(s) in block group 5 for inode table: Could not allocate block in ext2 filesystem

Relocating group 7's block bitmap from 229389 to 230408...

Relocating group 7's inode bitmap from 229390 to 230409...

Error allocating 512 contiguous block(s) in block group 7 for inode table: Could not allocate block in ext2 filesystem

Relocating group 9's block bitmap from 294925 to 295944...

Relocating group 9's inode bitmap from 294926 to 295945...

Error allocating 512 contiguous block(s) in block group 9 for inode table: Could not allocate block in ext2 filesystem

Relocating group 25's block bitmap from 819213 to 820232...

Relocating group 25's inode bitmap from 819214 to 820233...

Error allocating 512 contiguous block(s) in block group 25 for inode table: Could not allocate block in ext2 filesystem

Relocating group 27's block bitmap from 884749 to 885768...

Relocating group 27's inode bitmap from 884750 to 885769...

Error allocating 512 contiguous block(s) in block group 27 for inode table: Could not allocate block in ext2 filesystem

Relocating group 49's block bitmap from 1605645 to 1606664...

Relocating group 49's inode bitmap from 1605646 to 1606665...

Error allocating 512 contiguous block(s) in block group 49 for inode table: Could not allocate block in ext2 filesystem

Relocating group 81's block bitmap from 2654221 to 2655240...

Relocating group 81's inode bitmap from 2654222 to 2655241...

Error allocating 512 contiguous block(s) in block group 81 for inode table: Could not allocate block in ext2 filesystem

Relocating group 125's block bitmap from 4096013 to 4097032...

Relocating group 125's inode bitmap from 4096014 to 4097033...

Error allocating 512 contiguous block(s) in block group 125 for inode table: Could not allocate block in ext2 filesystem

Relocating group 243's block bitmap from 7962637 to 7963656...

Relocating group 243's inode bitmap from 7962638 to 7963657...

Relocating group 243's inode table from 7962639 to 7963658...

Relocating group 343's block bitmap from 11239437 to 11240456...

Relocating group 343's inode bitmap from 11239438 to 11240457...

Error allocating 512 contiguous block(s) in block group 343 for inode table: Could not allocate block in ext2 filesystem

Relocating group 625's block bitmap from 20480013 to 20481032...

Relocating group 625's inode bitmap from 20480014 to 20481033...

Relocating group 625's inode table from 20480015 to 20481034...

Relocating group 729's block bitmap from 23887885 to 23888904...

Relocating group 729's inode bitmap from 23887886 to 23888905...

Relocating group 729's inode table from 23887887 to 23888906...

e2fsck 1.41.11 (14-Mar-2010)

e2fsck: aborted
[/B]
```

I have searched extensively in the Ubuntu Forums and other Linux forums, and as of now I have no solution.

Does anyone have an idea how I can restore GRUB and my Ubuntu partition so that I can get  my system running again?

Thank you!

JBA2337    

P.S. Please excuse the length of this message. I thought that someone might see something in the e2fsck results that might be of help.

---

### Post by [Snc] on 2011-02-06
Please use the "code" section for the e2fsck output!

Edit your post, select the output of e2fsck and hit the "**#**" top right of the editor.

---

### Post by Rubi1200 on 2011-02-07
First thing to do is please run the boot info script and post the results here.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by JBA2337 on 2011-02-07
Here are the results of the boot info script:

```
title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8e1442281442141d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

proc /proc proc defaults 0 0
UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb / ext3 errors=remount-ro 0 1
/dev/sda3 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/JDiskC\040NTFS ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb2: Location of files loaded by Grub: ===================


 126.4GB: boot/grub/core.img
  93.3GB: boot/grub/grub.cfg
 117.5GB: boot/grub/menu.lst
 126.5GB: boot/initrd.img-2.6.31-21-generic-pae
 126.4GB: boot/initrd.img-2.6.32-22-generic-pae
 126.4GB: boot/initrd.img-2.6.32-23-generic-pae
 126.5GB: boot/initrd.img-2.6.32-24-generic-pae
 126.4GB: boot/vmlinuz-2.6.31-21-generic-pae
 126.4GB: boot/vmlinuz-2.6.32-22-generic-pae
 126.4GB: boot/vmlinuz-2.6.32-23-generic-pae
 126.5GB: boot/vmlinuz-2.6.32-24-generic-pae
 126.5GB: initrd.img
 126.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdc" to 4608
ERROR: hpt45x: seeking device "/dev/sdc" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdc" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdc" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdc" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdc" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdc" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdc" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdc" to 137438913024
ERROR: pdc: seeking device "/dev/sdc" to 137438920192
ERROR: pdc: seeking device "/dev/sdc" to 137438927360
ERROR: pdc: seeking device "/dev/sdc" to 137438934528
ERROR: sil: seeking device "/dev/sdc" to 18446744073709551104
ERROR: via: seeking device "/dev/sdc" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdc" to 4608
ERROR: hpt45x: seeking device "/dev/sdc" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdc" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdc" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdc" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdc" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdc" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdc" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdc" to 137438913024
ERROR: pdc: seeking device "/dev/sdc" to 137438920192
ERROR: pdc: seeking device "/dev/sdc" to 137438927360
ERROR: pdc: seeking device "/dev/sdc" to 137438934528
ERROR: sil: seeking device "/dev/sdc" to 18446744073709551104
ERROR: via: seeking device "/dev/sdc" to 18446744073709551104
```

Thanks for your help!
JBA2237

---

### Post by Rubi1200 on 2011-02-07
Are you sure this is everything from the RESULTS.txt?

There should be information that includes the partitions etc.

---

### Post by JBA2337 on 2011-02-07
Sorry, for some reason I did not submit all of the boot info script. Here it is.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 246906777 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 246906777 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   399,102,794   399,102,732   7 HPFS/NTFS
/dev/sda2         399,102,795   797,562,989   398,460,195  83 Linux
/dev/sda3         797,562,990   805,948,919     8,385,930  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   154,240,064   154,240,002   7 HPFS/NTFS
/dev/sdb2         154,240,065   304,174,709   149,934,645  83 Linux
/dev/sdb3         304,174,710   312,560,639     8,385,930  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8E1442281442141D                       ntfs       JDiskCntfs                    
/dev/sda2        148baf56-f6a2-4a93-82bc-44a3aa04a7fb   ext3       JDiskFext3                    
/dev/sda3                                               swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8E1442281442141D                       ntfs       JDiskCntfs                    
/dev/sdb2        148baf56-f6a2-4a93-82bc-44a3aa04a7fb   ext3       JDiskFext3                    
/dev/sdb3                                               swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb2/boot/grub/menu.lst: ===========================

# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro splash vga=791  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb ro single splash vga=791
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 148baf56-f6a2-4a93-82bc-44a3aa04a7fb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8e1442281442141d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

proc /proc proc defaults 0 0
UUID=148baf56-f6a2-4a93-82bc-44a3aa04a7fb / ext3 errors=remount-ro 0 1
/dev/sda3 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/JDiskC\040NTFS ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb2: Location of files loaded by Grub: ===================


 126.4GB: boot/grub/core.img
  93.3GB: boot/grub/grub.cfg
 117.5GB: boot/grub/menu.lst
 126.5GB: boot/initrd.img-2.6.31-21-generic-pae
 126.4GB: boot/initrd.img-2.6.32-22-generic-pae
 126.4GB: boot/initrd.img-2.6.32-23-generic-pae
 126.5GB: boot/initrd.img-2.6.32-24-generic-pae
 126.4GB: boot/vmlinuz-2.6.31-21-generic-pae
 126.4GB: boot/vmlinuz-2.6.32-22-generic-pae
 126.4GB: boot/vmlinuz-2.6.32-23-generic-pae
 126.5GB: boot/vmlinuz-2.6.32-24-generic-pae
 126.5GB: initrd.img
 126.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdc" to 4608
ERROR: hpt45x: seeking device "/dev/sdc" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdc" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdc" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdc" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdc" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdc" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdc" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdc" to 137438913024
ERROR: pdc: seeking device "/dev/sdc" to 137438920192
ERROR: pdc: seeking device "/dev/sdc" to 137438927360
ERROR: pdc: seeking device "/dev/sdc" to 137438934528
ERROR: sil: seeking device "/dev/sdc" to 18446744073709551104
ERROR: via: seeking device "/dev/sdc" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdc" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdc" to 4608
ERROR: hpt45x: seeking device "/dev/sdc" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdc" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdc" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdc" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdc" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdc" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdc" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdc" to 137438913024
ERROR: pdc: seeking device "/dev/sdc" to 137438920192
ERROR: pdc: seeking device "/dev/sdc" to 137438927360
ERROR: pdc: seeking device "/dev/sdc" to 137438934528
ERROR: sil: seeking device "/dev/sdc" to 18446744073709551104
ERROR: via: seeking device "/dev/sdc" to 18446744073709551104
```

---

### Post by JBA2337 on 2011-02-07
Just ignore the information for the sdb drive. That is an older drive, still in my computer. I installed a new Seagate drive and I cloned  the sdb drive to the new one, sda. The sda drive is now my primary boot drive, and it is the one that won't boot.

JBA2337

---

### Post by presence1960 on 2011-02-07
It looks like the clone attempt failed somehow. Since you have a working Ubuntu on sdb (it is working correct?), why don't you reclone it and try putting the cloned image on sda? I suggest [clonezilla]("http://clonezilla.org/"), but any method of cloning should work. Hopefully it won't foul up this time.

P.S. clonezilla will allow you to clone a partition as well as a disk.

---

### Post by oldfred on 2011-02-07
System is confused.

/dev/[COLOR=Red]sda2        148baf56-f6a2-4a93-82bc-44a3aa04a7fb[/COLOR]   ext3       JDiskFext3                    
/dev/sda3                                               swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8E1442281442141D                       ntfs       JDiskCntfs                    
/dev/[COLOR=Red]sdb2        148baf56-f6a2-4a93-82bc-44a3aa04a7fb[/COLOR]   ext3  

Since you cloned drives, you have same UUID. Not sure if then system configuration is confused on which drive is which. But you cannot mount two drives with same UUIDs.

I would first try unplugging old drive and see if then you can repair new.

---

### Post by matt_symes on 2011-02-07
Hi

Yup. The cloning failed badly from the looks of it. I would try again using presence1960's method.

Also you have some legacy Grub files kicking about. Remove them.

```
**/boot/grub/menu.lst** /boot/grub/grub.cfg /etc/fstab 
/boot/grub/core.img
```

Purge and reinstall grub when you have finished the cloning as you have an issue there are well.

Do as oldfred say's as well.

Kind regards

---

