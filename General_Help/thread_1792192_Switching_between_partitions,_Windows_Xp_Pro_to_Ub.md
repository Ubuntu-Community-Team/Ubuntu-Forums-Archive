---
title: "Switching between partitions, Windows Xp Pro to Ubuntu 11.04"
date: 2011-06-27
forum: General Help
---

### Post by Shvesley on 2011-06-27
I was running 11.04 as my main OS untill I installed Win Xp Pro. 50 GiB Ubuntu and 100 GiB Win Xp Pro. Now when ever I boot my computer (Acer Extensa 5620) it AUTOMATICALLY goes into the Win Xp Pro OS. So I have no idea how to access all of my Ubuntu files and programs etc. This is a really big problem as I have yet to hook up Win Xp Pro to the internet. It is an older OS and it has made things very difficult. So I really need to be able to switch OS partitions.

---

### Post by oldfred on 2011-06-28
When you installed XP, it automatically installed the windows boot loader to the MBR of the hard drive. You need to reinstall grub2's boot loader to the MBR and then run sudo update-grub to get windows added to the menu.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you need detailed help post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Shvesley on 2011-06-28
What does MBR stand for?

---

### Post by Shvesley on 2011-06-28
Master Boot Record. nvm

---

### Post by oldfred on 2011-06-28
Just to expound on Shvesley's answer. 

MBR is how all BIOS based computers boot. (Macs & some very new computers now use EFI or UEFI which is a newer way.) MBR has been used since the start of PCs 25 years ago. Computer starts up and reads the onboard ROM (now EEPROM) which has the BIOS. BIOS checks what hardware you have and if a hard drive is found it will jump to the primary master or boot drive to continue to boot. Then your operating system starts to load. But MBR is tiny so in most cases it just jumps to somewhere else after a few check and then loads more code from a partition.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

---

### Post by Shvesley on 2011-11-08
Can I just say, this thread has helped me more times than I can count. Thank you so much!

---

