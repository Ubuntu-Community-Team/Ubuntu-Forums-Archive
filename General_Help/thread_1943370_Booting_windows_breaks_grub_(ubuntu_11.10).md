---
title: "Booting windows breaks grub (ubuntu 11.10)"
date: 2012-03-19
forum: General Help
---

### Post by w0ss4g3 on 2012-03-19
Hi,

Have an odd problem with a dual boot install. After installing 11.10, the GRUB2 screen comes up - I can boot into ubuntu or Windows XP. If I boot into ubuntu I can reboot and grub comes back up as usual. However, as soon as I boot into windows then grub no longer loads, and the machine just continually reboots - doesn't even go into windows.

The only way to fix this is to boot from a liveCD or use the super grub2 disk - then I can find the grub install and load windows/ubuntu via that.

I've tried booting into the ubuntu install using the super grub disk and doing:

install-grub /dev/sda
update-grub

This fixes it so that grub loads again, however as soon as I boot windows again it's broken again. The only solution I've found so far is to use the super grub disk as my bootloader - not ideal!

However, it gives an error message along the lines of:

"Sector 5 is already in use by ZISD; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track" - Something to do with Novell Zenworks??


I've also tried a purge/reinstall of grub - no difference.

I'm guessing the Novell software is the problem.. can I just wipe the first 63 sectors and install grub again - or will this break the windows bootloader?

Any other suggestions?

Thanks in advance..

---

### Post by imachavel on 2012-03-19
when you get to the OS from the live cd, I don't suppose you have two cd drives do you? If so, you can download boot repair from here
 
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)
 
you could also install it using the terminal with ctrl+alt+t and try sudo apt-get install boot repair or sudo apt-get install boot-repair whichever works. Then go to the search bar in the top left corner of the desktop interface(I'm assuming you are using gnome or unity not kde since you booted to the live cd)
 
but the problem with this is it will address he grub created from the boot sector on the live cd. The live cd itself creates grub and everything you address from what you have booted will address this
 
download the .iso, burn a copy of boot repair from the link I provided. But this will only help if you have another cd or dvd rom drive that you can install the .iso to the cd, once it's downloaded by right clicking the file and selecting to burn to cd with I believe brasero disk burner(with windows magic iso works very well)
 
now if you can boot to the boot repair disk it will usually fix mbr and grub, even if dual boot is using different file systems(one is windows e.g. ntfs or fat32 the other is linux it will be ext2 or ext3 or ext4.) Funny enough I can't explain why the partition you use can only use ext2 or 3 or 4 file system, I'm not sure if it has something to do with the hdd, obviously this won't effect the swap partition at all.
 
you must select fix boot once booted to for this option. Now if you use sudo apt-get install boot repair then you can create a grub info script that will explain your
 
/dev/sda
 
or 
 
/dev/sdb (which will be something different then what you use for your primary drive, I forgot what /dev/ is)
 
and will show the boot flags. The problem as I've said is it shows the boot info for what is on the boot sector and the grub for the live cd you've booted to. But if you can boot into the linux partition on your dual boot, you could create a boot info script, and upload it as an attachment to this thread. What is on your other partition you are dual booting to? Can you boot to it?
 
If you have a friend who can remote in, on the live cd, maybe he could help you. I've heard team viewer opens with wine, but then you are facing an issue that you might need to forward ports for rdp(3389) or whatever team viewer uses. That is not actually a good idea, try seeing if you can download boot repair disk from another friends computer, and use it when the pc starts up. Or you could try it from the interface but that is probably not recommended

---

### Post by oldfred on 2012-03-19
Every time you boot into XP the Novell software must be overwriting the part of grub that is in the sectors after the MBR. 

This was(is) a known issue with grub2. They have worked around some of the Windows DRM software that writes into the boot area like Flexnet. They at least now give a warning. Before users just kept having issues. 

Do you have to have the Novell software? If so you may need to install grub2's boot loader to an external device like a USB flash drive, if you can boot from flash drives. Then you keep the Windows boot loader in the MBR of the internal drive and when you want to boot Ubuntu you use the flash just for the MBR boot.

---

