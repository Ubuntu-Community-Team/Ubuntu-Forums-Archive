---
title: "update-grub finds all Installs but booting doesn't show all of them?"
date: 2012-01-19
forum: General Help
---

### Post by joosca77 on 2012-01-19
Really stumped here. Installed multiple os's (I know I know.... stick with ubuntu ;)) when I run update-grub I get the following:
                                  Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-3.0.0-12-generic  
 Found initrd image: /boot/initrd.img-3.0.0-12-generic  
 Found memtest86+ image: /memtest86+.bin 
 Found Windows Recovery Environment (loader) on /dev/sdb1  
 Found Fedora release 16 (Verne) on /dev/sdd10  
 Found openSUSE 12.1 (x86_64) on /dev/sdd6  
 Found CentOS release 6.2 (Final) on /dev/sdd7  
 Found Arch on /dev/sdd8  
 
everything seems to run fine but when I reboot I only see "Ubuntu, Windows recovery, Suse, and CentOS"
Doesn't show anything about arch or fedora. I have tried boot-repair removing grub and adding it back to the /boot partition and everything boots fine excluding arch and fedora. Anybody have any suggestions? Thanks in advance!

---

### Post by oldfred on 2012-01-20
How big is the box or window that grub is using? Sometimes with many entries, it is more entries than the box and all you have to do is scroll down. You can see a tiny arrow on the right bottom of the box if you do have too many entries.

---

