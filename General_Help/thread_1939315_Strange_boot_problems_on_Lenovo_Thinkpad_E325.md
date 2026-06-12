---
title: "Strange boot problems on Lenovo Thinkpad E325"
date: 2012-03-11
forum: General Help
---

### Post by dsourcerer on 2012-03-11
I tried to install Ubuntu 11.10 to Lenovo laptop (I want to save Windows 7, which was preinstalled). But GRUB2 won't boot. So, I chrooted to new installed Ubuntu, and found out that grub-efi was installed. I googled and found that article:
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

I used this article and installed Ubuntu. It works well. But now I can't boot into Windows 7 (which is 32 bit), having a message "Invalid path to EFI" or something like it.  

I used Boot Info script ([http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)) and it's results are:
[http://pastebin.com/ejKJznxU](http://pastebin.com/ejKJznxU)

So, please, help :(

---

### Post by hakre on 2012-07-29
I can report that the same model (Lenovo E325) has booting problems with Ubuntu 12.04 LTS as well.

The standard as well as the manual install is just not able to deal with it.

I've then been running boot-repair as described on this blog-post: [http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

Before I applied this, I also created an extended (logical) partition to gain some free space for a grub booting partition (see detailed information about partitioning ubuntu on the german wiki pages for links and further explanations). Then I copied the Lenovo Rescure Recovery Partition from the end of the disk to the end of the extended partition. Then I deleted that original (and now duplicated) partition. Then I extended the new logical partition to the end of the disk and moved the rescue partition to the end inside the extended partition as well.

That allowed me to change the number of primary partitions to three so that just in case the boot partition required by grub (whether being EFI or legacy boot) technically possible.

In the bios I changed the boot procedure to first do legacy, then uefi. I did that change (as well as the partitioning) before running boot-repair.

So finally it worked.

What I strongly dislike about boot-repair is, that there is no information given what actually the problem is. I used the default option to just repair common problems. I mean it's nice but on the other hand I had liked to better understand what the issue is.

Anyway it works now. Looks like it uninstalls Grub 2 and installs Grub 1 again.

Anyway, I smell that Ubuntu 12.04 LTS is not yet ready for being flawless installed on Windows 7 Computers with UEFI Bios because after the "successfull" install, Windows is booting and Ubuntu - even installed - is not available to boot. No Grub, nothing.



The reporting paste is here: [http://paste.ubuntu.com/1117796/](http://paste.ubuntu.com/1117796/)

Backup as github gist: [https://gist.github.com/eec85580684e002798ca](https://gist.github.com/eec85580684e002798ca)

---

### Post by svrkispm on 2012-07-29
I have Lenovo E320. I had problems booting my ubuntu from usb key, fix was to set bios to legacy uefi boot (or something like that) and to mark my /boot partition as bootable using fdisk. This worked for grub 2 and also for grub.
No idea if this helps.

---

### Post by hakre on 2012-07-29
That's an interesting information. I discovered the BIOS options a little late so my first description might be doing too much in the end. However with that computer I could not turn back time (well I technically was able to because I had backups but I did not want to because of the time it takes to copy these X gigabytes all the time).

Probably switching the boot method priority from the default setting (UEFI+Legacy, UEFI first) to (UEFI+Legacy, Legacy first) might already solve the problem because the Ubuntu installer is able to work properly with it then.

I can recommend also to install from USB-Stick. I first had done with from an USB CD/DVD drive, but stick is much faster.

When I used the installer and the manual partitioning, I saw that per default the USB stick was set to be "GRUBbed" which technically makes no sense at all. No idea if that is part of the problem.

Another information: When I had selected "Legacy only" boot method in the bios, I was not able to boot from USB stick. No clue why.

I have **not** tried installing grub-efi package: [Precise won't boot on Lenovo E325 (Ubuntu Bugs; Bug #994184)](https://bugs.launchpad.net/ubuntu/+bug/994184) - because I did not know.

What I have learned so far, I can say the following:

[LIST]
[*] You can only have four (4) primary partitions, whereas Grub needs one and the extended partition is one, too. 
[*] The default Lenovo E325 System with Windows 7 comes already with three (3) primary partitions (1x Windows 7 Boot SystemDRV, 1x Windows 7 NTFS C:\ Drive, 1x Lenovo NTFS Rescue Drive)
[*] This default configuration has not enough room to add two more primary partitions at least (for dual/muli boot), which would be (at least): 1x Grub Partition, 1x Extended Partition (= 5, > 4 which does not work, there is a maximum of four primary partitions with legacy ).
[*] If you calculate size for the Grub partition, consider 250 MB as the UEFI boot part (if you like to use it) would require that (If I understood that right, but better safe than sorry when you're trouble shooting).
[*] The Windows 7 SystemDRV needs to be a primary partition, but the c:\ Windows 7 partition must not be (I read, link lost but I had this documented and printed)
[*] I could help myself with moving the "Lenovo Rescue and Recovery" primary partition into the extended one.
[*] The Ubuntu live CD comes with GParted that can do the diverse Partitioning Operations.
[/LIST]

***Note:*** The boot-repair program gave a hint, that the grub boot partition was a bit way not at the beginning of the disk so it could create some problems with some (older?) BIOSes. So probably it's wise to have some 250 MB space at the beginning of the drive for Grub. I don't know if this is a problem for Windows Boot, however IIRC that should be covered by windows repair. Probably windows repair is *not* available if you move the SystemDRV from the Harddisk itself, so you need the boot CD/DVD from the vendor (and the Lenovo device does not ship them, so contact support first, see next note on windows tax, too).

***Windows Tax:*** You need to once boot the Windows 7 copy on the Lenovo computer to create the Windows install DVDs (even only for backup purposes if you do not want to dump the disk). Instead you can also try to contact Lenovo (and stress them) to send you the DVDs (Lenovo has these DVDs, it is just that they are not eager to send them to everybody.). I'd say it's your right, you already paid the windows copy, so you've got the right to get the software in a format w/o installing it first (make it ready for first start), otherwise, you need to DD the disk first. Creating the DVDs on Windows itself requires you to accept the MS-EULA and some Lenovo-Terms which is a difference than just getting the software without accepting these terms. Maybe following recent EU legislation you're actually able to get some money back if you don't activate it for example, or at least more easily than with accepting it. In any case, if you delete it from the harddisk and sell the DVDs this is absolutely okay now in the whole EU, regardless of what the Lenovo terms say. If Lenovo tells you something different in support, ask them to specifically confirm in written language that the copy of the windows operating system is tighten to that specific computer. Then send me a private message on this board for contacting me by email.

---

