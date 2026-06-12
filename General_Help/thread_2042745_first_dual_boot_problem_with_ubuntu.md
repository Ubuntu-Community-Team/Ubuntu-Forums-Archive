---
title: "first dual boot problem with ubuntu"
date: 2012-08-15
forum: General Help
---

### Post by rookhusky on 2012-08-15
[RIGHT]alright, well i just installed Ubuntu 12.04 on my desktop, just before though i had put a nice new, clean installation of xp. after the Ubuntu installation though, when i select widows xp from GRUB it doesn't even seep to try to boot up i just get the blinking ASCII cursor, no hdd light flashing. I've never encountered a dual boot problem with any other distribution of Ubuntu, so i was wondering if you guys could impart some wisdom on me and help me out.  :confused:
[/RIGHT]

---

### Post by sienile on 2012-08-15
GRUB might have been improperly configured. You could try doing an update and see if that clears it up.

```
sudo update-grub
```

---

### Post by oldfred on 2012-08-15
Not sure sienile's suggestion will work. It sounds like you have an XP entry, but its XP that is not working.

This also does not fix XP issues but you can run the BootInfo report and post the link it creates. That may tell us what is wrong with Windows, or not.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by rookhusky on 2012-08-15
[just a status update]
sienile, thank you for your suggestion. but that did not fix it.
now I'm giving boot repair a go Oldfred. if that doesn't  get it, ill post my bootinfo

---

### Post by rookhusky on 2012-08-15
*sigh* heres my bootinfo [http://paste.ubuntu.com/1149413/](http://paste.ubuntu.com/1149413/)

---

### Post by oldfred on 2012-08-15
Since grub2's os-prober found the XP partition. I expected it to look ok. You can try chkdsk from a Windows XP install disk, but often Linux will not mount a NTFS partition that needs chkdsk.

You can also restore the two boot files. Boot.ini it in the boot script and it looks ok also.

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Boot files may need attributes also from Windows repair console where filename is each boot file:
attrib +r c:\filename
attrib +h c:\filename
attrib +s c:\filename

---

### Post by rookhusky on 2012-08-15
i can boot into ubuntu fine, in fact with 12.04 im seeing the fastest startup time ive seen yet with ubuntu, im gonna try running chkdsk from the setup disk. even tough the problem isint solved yet, id still like to thank you for helping me out, i know xp forwards and backwards, but im still not that well versed in linux yet.

---

### Post by rookhusky on 2012-08-15
is ther any way i could just reinstall windows on the partition the reinstall grub? out of curiosity since i seem to need to burn another setupdisk for windows to get to the repair menu, since i got my current one set up to skip it apparently (dont know why i would do that, but it seems i did)

---

### Post by oldfred on 2012-08-15
As long as the NTFS partition is NTFS and has boot flag it should just reinstall to that partition. It sound like you do not have much to back up but the standard be sure to backup everything before making system changes.

Windows will automatically install its boot loader, so you have to reinstall grub2's boot loader. You can use the gui version from Boot-Repair or manually update it with liveCD. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

From liveCD it is just two lines to reinstall grub2's boot loader. Mount partition with Ubuntu and grub install.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by rookhusky on 2012-08-15
well i installed the xp right before ubuntu so theres absolutly nothing to back up i still even have the drivers on my laptop, lemme go run the installations and the pop grub back on, ill report back with details

---

### Post by rookhusky on 2012-08-15
oldfred, should we ever meet in person id like to give you a firm handshake, both xp, and ubuntu are running fine now

---

### Post by oldfred on 2012-08-15
Glad you got it working.

Maybe my bucket list should include a world tour to collect all the handshakes, beers or coffees? :)

But it just is good to see users get an Ubuntu or other Linux system working.

---

