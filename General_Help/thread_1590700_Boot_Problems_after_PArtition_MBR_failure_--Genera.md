---
title: "Boot Problems after PArtition /MBR failure --General"
date: 2010-10-08
forum: General Help
---

### Post by vikrang on 2010-10-08
I had a tri boot of Win 7 /XP and Mint...I was using EasyBCD 2.0 as a boot manager...I booted Mint by configuring the NeoGrub option in Easy BCD..I wanted to uninstall Win 7 and so what I did was the following

1. Edited BCD bootloader settings ...Marked XP as my default and deleted Win 7 entry...
2. Logged out and wiped my Win 7 partition

With my fingers crossed , i rebooted but Easy BCD booted flawlessly with 2 choices XP and Mint(GRUB)...As Easy BCD is not meant for XP, I thought of restoring original NTLDR of XP so that things would be in place and thinking that this cud avoid problems of detection by other Linux OS

I deleted manually the Easy BCD menu.lst [[COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]file[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://ubuntuforums.org/#") and NeoGrub.mbr in my root...That was it , after I rebooted,

I got boot screen of EasyBCD but whichever option I select , I got an error message that address not Valid-NTLDR not found or something like that

I booted my XP live CD and like many times before ran

1.Fixmbr
2.Fixboot
3.bootcfg /rebuild

After that , now when I reboot , I am getting "Invalid Partition Table"

On booting from a linux CD , I can see the files are in place..I have to get boot sector and partition table fixed...Any ideas- perhaps I should use test disk? But the manual talks about recovering LOST partitions..I want to repair existing one...

---

### Post by srs5694 on 2010-10-08
Post the output of "sudo fdisk -lu" between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

