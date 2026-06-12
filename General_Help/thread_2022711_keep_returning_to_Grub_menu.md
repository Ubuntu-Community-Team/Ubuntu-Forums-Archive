---
title: "keep returning to Grub menu"
date: 2012-07-11
forum: General Help
---

### Post by Bjoessi on 2012-07-11
Hi,

I began asking at the Swedish ubuntu forum, but didnt get any advice that solved my problem: [http://ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=56662](http://ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=56662)

I am running a dual boot with Ubuntu 12.04 and winXP and they were booting nicely. At some point the WinXP boot has stopped working and I do not see any obvious change or upgrade that I have done.

Here is a dump created by Boot-Repair: [http://paste.ubuntu.com/1084855/](http://paste.ubuntu.com/1084855/)

The symptom/problem is that when I chose windows in the Grub menu, I end up back in the Grub menu, again asked to chose what to boot.

I have tried different settings in Boot-repair, and I have tried sudo update-grub with no change.

Any advice on how to proceed?

//Bjössi

---

### Post by sudodus on 2012-07-11
Have a look at the following link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

Maybe this chapter will help: **16. Restoring GRUB2 / XP / Vista / Win 7 Bootloaders**

or this link
[[COLOR="red"]_https://wiki.archlinux.org/index.php/GRUB2#Boot_Microsoft_Windows_installed_in_BIOS-MBR_mode_[/COLOR]]("https://wiki.archlinux.org/index.php/GRUB2#Boot_Microsoft_Windows_installed_in_BIOS-MBR_mode")

> Find the UUID of the NTFS filesystem of the Windows's SYSTEM PARTITION where the bootmgr and its files reside. For example, if Windows bootmgr exists at /media/Windows/bootmgr:

# grub-probe --target=fs_uuid /media/Windows/bootmgr
[COLOR="red"]69B235F6749E84CE[/COLOR]

Then, add the below code to /etc/grub.d/40_custom and regenerate grub.cfg with grub-mkconfig as explained above to boot Windows (Vista, 7 or 8) installed in BIOS-MBR mode: 

For Windows XP:

```
menuentry "Microsoft Windows XP" {
    insmod part_msdos
    insmod ntfs
    insmod search_fs_uuid
    insmod ntldr     
    search --fs-uuid --no-floppy --set=root [COLOR="Red"]69B235F6749E84CE[/COLOR]
    ntldr /ntldr
}
```

You must find and use the [COLOR="red"]UUID[/COLOR] for your Windows XP. It might be the XP partition or some recovery partition.

---

### Post by oldfred on 2012-07-11
You installed grub2 to the Windows NTFS partition. Windows NTFS partition are part of Windows boot and have to have a NTFS signature and specify either ntldr for XP or bootmgr for Vista/7.

> 
sda1: ___________________________________

    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 112215976 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Bjoessi on 2012-07-11
> **oldfred said:**
> 
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Brilliant! That did the trick! Thanks a million!

//Bjössi

---

