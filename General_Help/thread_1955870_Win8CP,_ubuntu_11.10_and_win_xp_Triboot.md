---
title: "Win8CP, ubuntu 11.10 and win xp Triboot"
date: 2012-04-10
forum: General Help
---

### Post by Geezanansa on 2012-04-10
Hi all

Trying to fix boot probs to any of three os's after windows xp installation.

What i have done is using a gparted live cd created 42GB partition (formatting it to ntfs) on 120GB hdd leaving 79GB to install Ubuntu 11.10 on. which i did after installing windows 8 consumer preview to the 79GB partition.(after previous goofed attempts:lolflag:)


Everything was running sweet.  Booted in and out of ubuntu no probs then tried to boot to windows 8.

I couldnt boot to windows( os cannot be found )and then had to use ubuntu desktop usb to get booted up again not sure what i did but on reboot i got the choice of booting to ubuntu or windows8 (ubuntu default)

can remember following a guide which made sure grub was installed using terminal for using and configuring grub for multiple os system..

Any hows did succeed in getting system reliably booting into os of my choice.


Then i thought how brilliant this is and if i could get gaming online;  (tried steam  wine pol etc and because win 8 is not released will get unknown api and booted)if i could get gaming fired up from same system.  Rather hav:lolflag:ng double the amount hardware and cables...


I had upgraded from xp to win8 on another system which is 32bit system and thought i would try reformatting and reinstalling xp from cd after connecting to my 64 bit machine to ide ribbon as slave and removed jumper to make slave.
This in my mind should have left me with win 8 /ubuntu drive as master with the grub choice at each boot.

after disconnecting xp hard drive and reconnecting (making sure cable and jumper set to slave) to ubuntu system thinking grub would update after booting to ubuntu but i could not boot to any os at all. This in my mind should have left me with win 8 /ubuntu drive as master with the grub choice at each boot.(boot to ubuntu and update grub and i should have had three os choices in grub menu list at next reboot)


after black screen with cursor(looks like ubuntu loader starting the bit when you press shift to get grub to load) all that returned was either no ntldr if i tried to boot to winxp and if i tred to boot win8 harddrive did not exist? and un recognised file system or rescue grub prompt if i tried to boot ubuntu but this no worky so try to boot from usb to fix ubuntu but would not load.

Managed to recover win 8 using installation/recovery media managed to recover xp but then tried to boot to ubuntu and  had to download and make fresh ubuntu desktop usb.

After much time and effort setting up my usb making it bootable using gparted live cd.  This learning curve has familiarised me with the terminology and tools to use for trying to fix my bootloader.  

After recovering windows 8 and ubuntu using boot repair tool/app from ubunt; the xp will not boot tried repair but no joy.
No ntldr
 
 
So after reinstalling xp i have lost win8 and ubuntu again so
 
 
How would one install win8 and ubuntu on one hdd and then xp on second hard drive all in the same system?
 
I have read in older systems on ide ribbon slave drives will not boot.
 
Looking for a bit of encouragement and guidance seem to be fumbling about in circles.
 
Have learned different OS's all have different boot loaders or ways of managing start up.(or at least these three do)
 grub manages this
 
I want ubuntu to be default OS so i post in these forums
 
Thanks in advance

---

### Post by Mark Phelps on 2012-04-10
When dealing with different generations of MS Windows OSs, you MUST install the earlier versions first.  Each newer version is able to read and understand the booting needed for the older versions -- but not the other way around.

So, to make this work, you would have to use the order:
1) XP
2) Win8CP
3) Ubuntu

But, I'm not sure that will work when done, because you will have to run os_prober in Ubuntu to find the Windows OSs, and from what I've seen, MS has changed the Win8 boot loader so much that Linux doesn't recognize it anymore.  So, you won't get a GRUB menu that includes Windows 8 in it (and probably, NOT XP as well).

---

### Post by Geezanansa on 2012-04-11
I am working on what you recommend.
Apparently if you install XP first then windows 8 cp the new OS handles the bootloader for xp
you boot to win 8 advanced start up options by pressing F8 as soon as the bootloader prompt appears(just like pressing shift to get grub to load)
 
There are boot flags and other settings to tweak once ubuntu is installed on other hard drive.
 
Once grub is installed and updated on reboot windows recovery environment(loader) gets listed with linux kernels etc
 
I am working on getting xp and 8 on same hdd on different partitions.
 
Then will make sure i can boot from win 8 to xp
 
Then install ubuntu on second hdd.
 
Then use boot-repair to tweak bootloaders/mbr
 
it is apperently possible to set grub show win xp win 8 and ubuntu choice at boot using boot repair or command if you know what your on! There is another boot/loader/manager cfg tool for ubuntu but will have to go looking. I am sure a member narkod or darknod or something has or used to have link in his/her link.
 
If at first you don not succeed. Ask; why?...:lolflag:
 
On my previous attempts i had used gparted and gparted live cd to resize partitions and format which ithink has been one of the factors stopping things working.
 
This time after installing xp (using installation media to format partition) i used easeus partition master 9.1.1 to format, resize, relabel and rename drives within windows.
 
Still ongoing-thought i would do updates before going for win 8 installation.
 
There are two methods of getting win 8cp on different partition setup.exe and .iso.  not sure if this is significant for getting win8cp to show other windows versions.
 
This is relevant for ubuntu installation to get triboot so just trying to share what i been learning.

---

