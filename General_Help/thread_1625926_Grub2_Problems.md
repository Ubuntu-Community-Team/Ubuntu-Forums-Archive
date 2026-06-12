---
title: "Grub2 Problems"
date: 2010-11-19
forum: General Help
---

### Post by DevinMcElheran on 2010-11-19
I had Ubuntu installed on my desktop, then installed Windows 7, which, as usual, recked my MBR. So then, I "fixed" it by booting LiveCD. Then when I booted Ubuntu off of my hard disk, I used the command "sudo update-grub2".

This seemed to work, it recreated my grub menu and such. But the problem lies when I go to boot windows, when I try I get a blank screen, then a second or two later I get "Missing Helper", and that's it, it hangs there with a blinking insertion point at the end.

This is my Windows 7 block of my grub.cfg

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 863680d53680c81f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

Does anyone see anything wrong with it? Before I installed Windows 7, I had Vista, I formatted my partition and did a clean install. I think I played with my partitions a bit too, I have my Ext4 for Ubuntu, then NTFS for Windows, and a FAT32 for all of my files for accessing between each OS. I might have made the FAT32 bigger and the NTFS smaller, and leaving the Ext4 untouched.

Any help would be greatly appreciated, thank you.

---

### Post by oldfred on 2010-11-19
I looked up the error and that is a windows error. Grub has booted windows just like the windows MBR would boot it. You have a windows error not related to grub.

Missing Helper
[http://pcsupport.about.com/od/findbyerrormessage/a/helper-dll-not-found-missing-error.htm](http://pcsupport.about.com/od/findbyerrormessage/a/helper-dll-not-found-missing-error.htm)

In moving partitions around perhaps the windows install is not clean and needs repair. Sometimes just running chkdsk works, othertimes you need to go thru the full windows repairs. 

oldfred's Windows repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)
Info & adding XP after 7  for windows setup, USB flash drive for repair, shows windows 7 repair menu screen

I do not recommend FAT for data anymore. Too many files are larger than 4GB and copying a large file to FAT will just truncate it and you will never know it was destroyed. Use NTFS. Plus NTFS is journalized so repairs are possible with chkdsk or other tools.

---

