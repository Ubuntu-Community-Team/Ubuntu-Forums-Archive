---
title: "No MBR to boot from and no lilo config file"
date: 2011-10-09
forum: General Help
---

### Post by xXxG0dzRagexXx on 2011-10-09
I deleted my ubuntu partition so i can gain some space back in to my windows 7 partition. Since i deleted GRUB i cant boot my computer and i read something about installing lilo. 

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

I read the readme and it is telling me to edit the lilo config file in /ect/ and its not there. Now i just really want to fix my computer so i can use it. I dont want the lilo bootloader anymore since it seems like such a hassle. Can someone help?

---

### Post by xXxG0dzRagexXx on 2011-10-09
Can i just use ubuntu and reinstall it so that grub over writes the lilo bootloader.?

---

### Post by claracc on 2011-10-09
You don't need to install other boot manager, you can boot windows from the own win 7 disk:

[http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html](http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html)

---

### Post by xXxG0dzRagexXx on 2011-10-09
> **claracc said:**
> You don't need to install other boot manager, you can boot windows from the own win 7 disk:

[http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html](http://www.sevenforums.com/backup-restore/62209-remove-grub-restore-windows-7-a.html)

Yeah the only problem is i dont have a win 7 disk or a DVD to burn one. i tried doing ms-sys but i couldnt get it to install. my next thing i was gonn ado was use supergrub to fix it but i wanna make sure that this boot manager (which i found out is outdated) wont screw anything up worse then it is

---

### Post by claracc on 2011-10-09
Take a look to this link: [http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

Perhaps you can recover your mbr win boot with it.

---

### Post by xXxG0dzRagexXx on 2011-10-09
> **claracc said:**
> Take a look to this link: [http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

Perhaps you can recover your mbr win boot with it.

Well it looks like its for dual booting and i dont really dual boot anything. Now if i had to dual boot ubuntu with it to fix it i would be fine. because atleast i know what im dual booting with.

---

### Post by xXxG0dzRagexXx on 2011-10-09
so my laptop ended up turning itself off and now my laptop screen doesnt show anything at all when it boots up. ugghhh I have a feeling my laptop is forever screwed.

---

### Post by xXxG0dzRagexXx on 2011-10-09
Can anybody please help me?

---

### Post by mike555 on 2011-10-09
If you can't boot you might try PLOP boot loader, but if you went into your mbr and deleted grub you have a problem (I'm not sure you can delete grub that way) probably better to borrow a Windows disc and fix mbr

---

### Post by xXxG0dzRagexXx on 2011-10-09
Well I tried creating a system repair disc but it's a windows 8 dev one. I was still hoping that my computer would boot right in to it and at least tell me that but when I press the power button nothing comes up. Before LILO and it was just grub that was deleted it went to the HP screen  and I could press escape for boot options so I can boot to a CD. That's how I was on the Ubuntu install disk. But nothing comes up now. The mo itor doesn't even turn on. (BTW this is a laptop I'm working with)

---

### Post by oldfred on 2011-10-09
Both lilo & the windows boot loaders use the boot flag (active partition in windows) to know where to chainload to.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

From windows you need the fixMBR command:
How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands (# is just a comment, do not type that:

BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Fixed title to MBR

---

### Post by xXxG0dzRagexXx on 2011-10-09
Thanks for trying to help but I can't boot in to the installation disc of Ubuntu to restore the windows boot loader.

Also How can I boot in to the installation disk when my computers LCD doesn't even go on?

---

### Post by oldfred on 2011-10-09
Does LCD work with BIOS? If so then you may need nomodeset or other parameter to boot with.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by xXxG0dzRagexXx on 2011-10-09
It seems that I can't even get in to my bios. F10 is suppose to be my bios and i turn on the laptop and press it repeatedly but nothing. LCD does turn on at all. :(

---

### Post by oldfred on 2011-10-09
Try removing battery and full reset. If still no LCD then it sounds like system hardware is the issue.

---

### Post by xXxG0dzRagexXx on 2011-10-09
OHKAY OHKAY OHKAY. do I unplugged the battery and put in the charger. Magically. It turned on and went to the HP screen and I went to bios. I'm hoping on next boot up I can run ubuntu and either install for grub or get my windows boot loader back.

---

### Post by xXxG0dzRagexXx on 2011-10-09
Oh hahaha. OHKAY I guess I did what you recommended on my own.  :Po

---

### Post by xXxG0dzRagexXx on 2011-10-09
Does anybody now what I should do now?

---

### Post by drs305 on 2011-10-09
I was just experimenting with Lubuntu on an old laptop this afternoon and couldn't get the screen to display once I selected "Try Ubuntu". Even though it was a laptop with no special video, it would blank once I made my initial selection. No cursor, no nothing. (In fact, I'm pretty sure it had booted but of course I couldn't tell.)

I eventually got it to boot to a visible Desktop after I selected the language and on the next screen pressed F6, selected 'nomodeset' (it will place an x next to it), and then booting. I didn't expect 'nomodeset' to really work since it was such a basic laptop (and I assume basic video), but it did in my case. 

If it doesn't boot to the Desktop but does get you to the command line, you can still install lilo from there and run the commands presented earlier to get back your Windows bootloader.

As a side note, I earlier in the day had the same symptoms and determined it was a bad burn.

---

### Post by xXxG0dzRagexXx on 2011-10-09
I've decided to just go ahead and dual Ubuntu and windows 7 again for right now. But I have no idea how to do the partitioning. I'm manually creating the partition for it and I know it needs to be a primary partition but I don't know if it should be at beginning or end, mount point, or type. I think it's suppose to be ext4 but I need help. Plus I need to add the swaps.

---

### Post by xXxG0dzRagexXx on 2011-10-09
I've gotten in impacient and I just created the partition and now I just want to know where should the boot loader be installed?

---

### Post by drs305 on 2011-10-09
> **xXxG0dzRagexXx said:**
> I've gotten in impacient and I just created the partition and now I just want to know where should the boot loader be installed?

If you are dual booting Windows and Ubuntu on the same drive, normally Grub is installed to the MBR of the drive (sda if it's the first drive).

If you are dual booting and the OS's are on different drives, install Grub to the MBR of the Ubuntu drive and set the BIOS to boot the Ubuntu drive first. This will leave the Windows drive MBR untouched; if for some reason Grub fails you can still boot Windows by changing the BIOS boot order back to the Windows drive and using the Windows bootloader.

---

