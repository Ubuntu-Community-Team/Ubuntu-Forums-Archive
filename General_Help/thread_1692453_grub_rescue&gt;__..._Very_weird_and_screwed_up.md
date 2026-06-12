---
title: "grub rescue&gt;_ ... Very weird and screwed up"
date: 2011-02-21
forum: General Help
---

### Post by PrvSAT on 2011-02-21
Hi, :KS

I've read about booting problems but could not find one that is similar with what I have:
- I had Ubuntu 10.04 running on a disk and windows 7 on another disk.  They were completely independent, no grub menu to select from a booting  menu. When I installed Ubuntu, I have physically unplugged the Windows  drive. I wanted to keep them completely separated. At boot I could  select from BIOS which is the booting drive so I could boot  independently from each drive. Everything was perfect.

- In W7, I've made a complete backup using Windows Backup resulting in a  complete image and a booting "recovery disk". With that I considered  that any screw up could be fixed at any time but I was wrong... (see further).
- In Ubuntu I've made a complete backup using Clonezilla disk (excelent and reliable backup s/w).

- I wanted to try out a clean Maverick 10.10 so I have installed it over  existing ubuntu but I forgot to unplugged the windows drive so at boot I  had a grub menu asking where to boot from, a linux or windows. I did  not wanted a grub menu to select the OS to boot from.

So here is is what happened: I have unplugged the windows drive and  reinstalled ubuntu. Booting in newly Ubuntu, it was OK except when you  try to boot from Windows drive you get a a prompt "grub rescue>_" and  that's it! No booting from windows anymore! 
I guess ubuntu wrote some data in the booting sector of the windows  drive and since I had to reinstall ubuntu with the drive unplugged, did  not find it anymore. I was very pissed. 

Having the windows backup I considered there is no problem. I have  booted from ubuntu, went to "Disk Management" and completely erased the  windows disk, then re-created the same NTFS partition and then format.
Started with Windows recovery disk, it found the image where it was  saved (on another disk) and started the restore process. After  successful restoration, reboot as windows to be primary hard drive and I  get the same damned prompt: "grub_rescue>"

I did not know that ubutnu is writing something to the boot sector on a  windows drive. Why does it do that? How come after erasing the content,  re-partition, re-formatting, restoring of the windows disk, I still get  this prompt?
Could anyone please suggest how should I fix this please?

---

### Post by PrvSAT on 2011-02-21
I was able to restore the windows boot by booting from the rescue disk, entering in dos prompt and typing:
bootrec.exe /fixboot
bootrec.exe /fixmbr
Reboot normally and windows is now fixed!

This was thanks to the following threads:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

