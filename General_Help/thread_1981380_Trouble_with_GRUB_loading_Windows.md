---
title: "Trouble with GRUB loading Windows"
date: 2012-05-16
forum: General Help
---

### Post by airspoon on 2012-05-16
Hello, I recently built a machine with two SSDs, so I decided to throw Win 7 Pro on the second SSD for a few games (with Ubuntu 12.04 on the first SSD). However, GRUB is not loading the windows disk, but instead it's kicking back an UEFI error (I forget the exact wording of the error). I tried updating grub and nada. Same error and failure to load. Is there a trick to this or a possible solution? 

As it is right now, I'm having to go into UEFI in order to select the disk that I want to boot, though that's a pain in the rear, considering that the UEFI loading screen is only visible for a split second at most (sometimes not at all). If my reflexes aren't rock-solid with each reboot of the machine, it brings me into GRUB where I can only boot into Ubuntu. I don't boot into Windows all that often, really only to use STEAM and Adobe but with the extremely high financial "investment" to get Windows running on my machine, I'm hoping that there is someway to get GRUB to recognize the Windows installation.

Any and all help would be greatly appreciated. Thanks....

---

### Post by wilee-nilee on 2012-05-16
> **airspoon said:**
> Hello, I recently built a machine with two SSDs, so I decided to throw Win 7 Pro on the second SSD for a few games (with Ubuntu 12.04 on the first SSD). However, GRUB is not loading the windows disk, but instead it's kicking back an UEFI error (I forget the exact wording of the error). I tried updating grub and nada. Same error and failure to load. Is there a trick to this or a possible solution? 

As it is right now, I'm having to go into UEFI in order to select the disk that I want to boot, though that's a pain in the rear, considering that the UEFI loading screen is only visible for a split second at most (sometimes not at all). If my reflexes aren't rock-solid with each reboot of the machine, it brings me into GRUB where I can only boot into Ubuntu. I don't boot into Windows all that often, really only to use STEAM and Adobe but with the extremely high financial "investment" to get Windows running on my machine, I'm hoping that there is someway to get GRUB to recognize the Windows installation.

Any and all help would be greatly appreciated. Thanks....

Run these commands in Ubuntu and a results.txt will show in the Ubuntu home, copy and paste the text to a reply. Use code tags in the reply by clicking the # in the reply and paste the code between what is generated which looks like this [ code][/code]

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by oldfred on 2012-05-16
Not many of us know UEFI as it is so new. But I think the idea of UEFI is that it is in control and you use it to boot as everyone's boot file is in the efi partition. Not sure about multiple drives.

I have these links.

[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
[http://ubuntuforums.org/showthread.php?t=1746194](http://ubuntuforums.org/showthread.php?t=1746194)

---

