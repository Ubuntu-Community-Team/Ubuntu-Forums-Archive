---
title: "(help!)Reinstalling ubuntu grub bootloader"
date: 2011-07-13
forum: General Help
---

### Post by adeee on 2011-07-13
Guys i have dual boot. and now i want to reinstall the windows xp. and there is a problem. if i install the windows, widows will wipes out the entire disk and hide the ubuntu. then definatly i may need to reinstall again ubuntu grub boot loader.
How can i do this via Live CD?
i found an article. [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

is this right way?
and what is my first hard drive? i cant figure out where i install grub? 
ya its very noob question. but i only know i install grub on /dev/sda6 and in the tutorial i cant understand hd0, 0 what is it? 
in this manner what is my grub location.

here is a screenshot of my Gparted filesystem 

[ATTACH]197382[/ATTACH]

help require.

---

### Post by Mark Phelps on 2011-07-13
You've got THREE NTFS partitions, and my guess, is that you have XP installed to the first one -- since it has the boot flag set.

You SHOULD be able to tell XP to use just that partition when you boot from the CD and attempt to reinstall it.  That will not wipe out any other partitions.

You WILL then have to reinstall GRUB as the XP reinstall will reset the MBR code, removing the GRUB reference there.

---

### Post by oldfred on 2011-07-13
Do you have grub legacy (0.97)? If so then your link is ok. But if you have grub2 from a new install of 10.04 then you need to use the grub2 reinstall instructions which are totally different.

Grub legacy refers to drive & partition as hd0,0. Grub 2 uses hd0,1 for first partition or sda1.

Do not reinstall grub or grub2 to a partition but to the MBR of sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by adeee on 2011-07-31
the procedure mention above is not working. and my ubuntu is totally hide. am currently on windows. so how can i retake the ubuntu?

---

### Post by oldfred on 2011-07-31
You also have a separate /boot so you have to mount it as part of the reinstall procedure. That is why we normally suggest not to have a separate /boot for most desktops. Servers and very old systems may need the separate /boot.

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

