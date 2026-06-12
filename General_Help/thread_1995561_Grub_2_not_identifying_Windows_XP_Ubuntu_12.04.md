---
title: "Grub 2 not identifying Windows XP Ubuntu 12.04"
date: 2012-06-03
forum: General Help
---

### Post by elecimpulse on 2012-06-03
Hi I have recently did a clean Ubuntu 12.04 install & lost Windows XP from the grub menu.

I have tried several tools such as boot repair to fix the problem but no luck. I looked at various threads and tried to add Windows manually; after which windows appears in the menu but shows an error "no argument defined" & "cannot get values C/H/S on hd1"

My 40_custom file is as follows:
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change

# the 'exec tail' line above.
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set FA2465A924656999
    drivemap -s (hd1) ${root}
    chainloader +1
}
#FOUND THIS ENTRY SOMEWHERE (doesnt work)--
#menuentry "Windows XP" {
#insmod part_gpt
#insmod fat
#insmod search_fs_uuid
#insmod chain
#set root='(hd0,gpt3)'
#search --fs-uuid --no-floppy --set=root FA2465A924656999
#chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
#}

Details of the grub command & bootrepair results- [http://paste.ubuntu.com/1021992](http://paste.ubuntu.com/1021992) 
Gparted result attached.
Any help would be appreciated. :)

---

### Post by oldfred on 2012-06-04
Your Windows boot partition sda1 is missing boot.ini.

So any entry you add to 40_custom will not work. And sudo update-grub will work once you create a boot.ini.

If you use Ubuntu to create boot.ini realize line ending in Linux & Windows are different. Save in Windows mode.

You can find example boot.ini in every  boot script with XP. or use your Windows XP CD to recreate one.

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
BOOTCFG  /rebuild  # rebuilds boot.ini

If os-prober on a sudo update-grub finds these files, then it will add the boot entry:
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

---

### Post by elecimpulse on 2012-06-04
WOW Thanks Old Fred. It worked !! :D

I lost my XP disc so while I started researching on creating a new boot.ini for XP, I did a search for the file in Windows partition and found boot.ini.backup (I might have used a recovery software or Windows might have created that itself)

Copied boot.ini.backup renamed it and copied it to the root of Windows partition.

After this I ran boot-repair which runs update-grub and all sorts of commands and restarted n Hurrah!! A new entry to the Grub menu which worked. !!
Thanks alot !! I'll mark this thread as solved.

---

