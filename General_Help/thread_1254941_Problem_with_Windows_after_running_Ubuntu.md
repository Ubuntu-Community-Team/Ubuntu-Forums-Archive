---
title: "Problem with Windows after running Ubuntu"
date: 2009-08-31
forum: General Help
---

### Post by IIv_SHaDoW_vII on 2009-08-31
I have searched all over the Internet and can't seem to find a valid answer for my problem. I recently installed Ubuntu on my system and it's fine for about a day but when I try to boot Windows it will try to load and then give me the error message 
<Windows Root>\system32\ntoskrnl.exe not found.

Here is a more descriptive version of above.
I installed Ubuntu via LiveCD on the second partition of my first harddrive. I have 2 harddrives total and both are sata with no jumpers installed. The first hd (250gb Maxtor) has Windows XP PRO SP3(NTFS) on the first partition, Ubuntu 9.04 (ext4) on the second partition, and the swap at the end of the first hd. My second harddrive (400gb WD) is one full partition as (NTFS) used for storage. Both drives are primary drives.
My BIOS settings for the access mode on both harddrives is set to auto. 

Basically what happens is, I am able to run both Windows and Ubuntu at first, however, when I boot Ubuntu and do something (I am not sure what?), it causes Windows to become unloadable from the Grub bootloader. It does not erase the Windows entry, it just displays the error message mentioned above which shows that the actual Windows loader cannot find the files to boot. My theory is, I am corrupting it because I am mounting the Windows partition in Ubuntu which I remember doing both times it corrupted.. however, I have searched and many people say its ok to do that so I don't know what the problem is.

To fix the problem I run the Windows Install CD and run FIXMBR, this overrides the grubloader and fixes Windows. I then reinstall grub to get it to work again. While this fixes the problem temporarily.. it gets annoying. Any help on permanently fixing this problem would be greatly appreciated.

---

### Post by NoaHall on 2009-08-31
It seems to be a error with your kernel. Are you doing anything to "hack" Windows? Attempting to force pae, etc.

---

### Post by anujpathania on 2009-08-31
Put in a clean windows install and try Wubi that comes on Disk. It handles most of the dual booting issues in a elegant way.

---

### Post by IIv_SHaDoW_vII on 2009-08-31
Hi, no I am not doing anything to hack Windows.. This has happened with fresh installs of Windows and Ubuntu. The Ubuntu disk found no disk errors and Windows boots and runs fine before I install Ubuntu again. It will load with grub a few times.. but I am doing something while in Ubuntu that messes it up.. I think its due to me mounting the windows partition. 

I will look into Wubi.
EDIT: I would rather not run Ubuntu as an application inside Windows. I appreciate the suggestion as it may be what I have to do.. However, I would rather fix the problem.

[[ubuntu] GRUB won't load windows [Archive] - Ubuntu Forums]("http://ubuntuforums.org/archive/index.php/t-1123220.html") 
I found this thread on the forum and it seems to be the exact same problem I am having. Someone in the thread said the problem is with the Grub bootloader and I have to agree as its happened 3 times now regardless of how it is installed. Windows runs great before installing Ubuntu so I think I will try either reinstalling grub or finding an alternate bootloader. Any more help would be appreciated.

---

