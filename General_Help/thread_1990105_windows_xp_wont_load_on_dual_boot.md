---
title: "windows xp wont load on dual boot"
date: 2012-05-29
forum: General Help
---

### Post by claire14 on 2012-05-29
hi i made a partition to dual boot windows xp from ubuntu 11.10 
and when i put windows xp on it to start the dual boot it gives a hard drive error , windows has shut down to stop any damage been done to your pc , windows is ok on virtual box, i did all the fixes to make virtual box run faster ,  but its to slow on netflix so i have to dual boot , i ran a full hard drive check and it checked everything and gave no errors , why is it giving a hard drive or you have other devices installed errors :( 
the guide to dual booting said to save grub first is that all i have to do 
does anyone know how to fix this :)
thankyou if you can

i did everything from this thread to fix virtual box [http://ubuntuforums.org/showthread.php?t=1904636&page=2](http://ubuntuforums.org/showthread.php?t=1904636&page=2) but its still slow

---

### Post by kc1di on 2012-05-29
hi sorry your having problems. 

go to this page and download and run boot repair. 
think it may work for you.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Never mind didn't see that your using virtual box. 
Sorry ;)

---

### Post by claire14 on 2012-05-29
> **kc1di said:**
> hi sorry your having problems. 

go to this page and download and run boot repair. 
think it may work for you.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Never mind didn't see that your using virtual box. 
Sorry ;)

hi the dual boot is a real dual boot , i have virtual box to but its just too slow for netflix :( 
Linux did everything untill DRM messed things up :(

thankyou for the Link :) 
do you know how to save grub on ubuntu 11.10 the instructions i have are for 9.04 will they be still ok

---

### Post by kc1di on 2012-05-29
Boot repair should take care of it for you. 

the instructions for 9.04 if I'm not mistake would have been for grub Legacy and with 10.04 they moved over to Grub2 so no don't think they would be applicable at this time.
not exactly sure what you mean by save grub here is a page that explains all you need to know about grub 2

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by claire14 on 2012-05-29
> **kc1di said:**
> Boot repair should take care of it for you. 

the instructions for 9.04 if I'm not mistake would have been for grub Legacy and with 10.04 they moved over to Grub2 so no don't think they would be applicable at this time.
not exactly sure what you mean by save grub here is a page that explains all you need to know about grub 2

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

hi thankyou again , this is the link that says to save grub
 [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2)

---

### Post by claire14 on 2012-05-29
hi boot repair hasn't fixed it , it still gives the same error 
can anyone fix this

---

### Post by wilee-nilee on 2012-05-29
> **claire14 said:**
> hi boot repair hasn't fixed it , it still gives the same error 
can anyone fix this

Post the boot summary that the boot-repair generates and concisely say what the problem is please.

---

### Post by claire14 on 2012-05-29
> **wilee-nilee said:**
> Post the boot summary that the boot-repair generates and concisely say what the problem is please.

hi this is the boot repair report [http://paste.ubuntu.com/1013370/](http://paste.ubuntu.com/1013370/)

, i will get the error codes from windows and post it to

error codes on windows xp are
0x0000007B (0XF78D2524 , 0XC0000034, 0X00000000 , 0X00000000 )
with a check for viruses and hard drives or hard drive controllers and RUN CHKDSH/F TO CHECK FOR HARD DRIVE CORRUPTION message , i can get a screen shot of it later when i get to a cam if its needed

---

### Post by wilee-nilee on 2012-05-29
> **claire14 said:**
> hi this is the boot repair report [http://paste.ubuntu.com/1013370/](http://paste.ubuntu.com/1013370/)

, i will get the error codes from windows and post it to

The script shows a pretty messed up hard drive setup, XP is not even showing, except in a small reference in a Linux type partition.

Might you consider backing up the linux and just wiping the Hard drive and starting over correctly partitioning and installing?

---

### Post by claire14 on 2012-05-29
if thats the only fix then that's what i will have to do

---

### Post by kc1di on 2012-05-29
I agree your best course is to wipe the drive and start over.
back up what you can. 

Install windows xp first then Ubuntu.

here another Link that will explain it for  you.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

that original link you posted that told you to save grub was for grub legacy not the new grub2.

---

### Post by wilee-nilee on 2012-05-29
> **claire14 said:**
> if thats the only fix then that's what i will have to do

I would say in order to have future problems yes, do you know how to do this. 

The XP should be in  NTFS and be the first partition, which it is now but with a higher partition number than the Linux. 

The XP shows a sda3, linux sda1, you really want these consecutive and the installed in a correct partition type.

XP as it shows on the script does not seem to be fixable.

The NTFS Should be active, it would show a boot flag in gparted on its partition.

You could clone the Linux if you were keen to this and slip it back in, as it is, with the partition numbers correct.

---

### Post by claire14 on 2012-05-29
> **kc1di said:**
> I agree your best course is to wipe the drive and start over.
back up what you can. 

Install windows xp first then Ubuntu.

here another Link that will explain it for  you.

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

that original link you posted that told you to save grub was for grub legacy not the new grub2.

thankyou for the help :)
i will probably be back later on windows :) and dual boot later

---

