---
title: "boot directly into 11.04 instead of XP ..... again"
date: 2011-07-30
forum: General Help
---

### Post by nichos on 2011-07-30
Now that I managed, with your help ofcource, to use F.Fox, write letters, print wirelessly, network, use yutube & manage fotos in Linux (except for FSX I boot XP) I would like Linux priority in the 1st menu.

On booting I get the 1st menu below, XP? or Ubuntu?,
If I do nothing boots into XP, if I select Ubuntu I get the 2nd menu.

What shall I transpose so that I get in the 1st menu Ubuntu priority?.

1st)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

2nd)

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
Asus P5K Premium WiFiiFi Intel Core 2 Quad Pro 2.4GHz, OCZ Vendetta Cpu Cooler, 2x2GB, DDR2 800 PC2-6400, GeForce 9800 GTX (PCI-E), sata 250gb, OCZ 600W Psu, X45, XP sp3, Ubuntu 11.04

---

### Post by snoopo71 on 2011-07-30
> **nichos said:**
> Now that I managed, with your help ofcource, to use F.Fox, write letters, print wirelessly, network, use yutube & manage fotos in Linux (except for FSX I boot XP) I would like Linux priority in the 1st menu.

On booting I get the 1st menu below, XP? or Ubuntu?,
If I do nothing boots into XP, if I select Ubuntu I get the 2nd menu.

What shall I transpose so that I get in the 1st menu Ubuntu priority?.

1st)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

2nd)

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
Asus P5K Premium WiFiiFi Intel Core 2 Quad Pro 2.4GHz, OCZ Vendetta Cpu Cooler, 2x2GB, DDR2 800 PC2-6400, GeForce 9800 GTX (PCI-E), sata 250gb, OCZ 600W Psu, X45, XP sp3, Ubuntu 11.04


Hi! Ok, first of all which grub do you use? I guess grub2, in that case, first of all make a backup of your menu.lst:
-  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

Then edit your menu.lst:
-  sudo gedit /boot/grub/menu.lst

Find the line: default  0

Then replace the 0 with the number on the startup list corresponding to the option you want, counting from 0.


Startup list example:
title      Ubuntu, kernel 2.6.15-27-amd64-generic  #this would be 0
...
title      Ubuntu, memtest86+   #this would be 1
...
title      Other operating systems:   #this would be 2
...
title      Microsoft Windows XP Home   #this would be 3

Good luck!!

---

### Post by OldBoy44 on 2011-07-30
Hi, I don't think moderators take too kindly to double posts! :)

---

### Post by nichos on 2011-07-31
Thanx Snoopo,

That command does not exist terminal says.

The 2nd boot menu I get is the Linux one:-

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Is this one needing change?, can you type it here how it should be changed please?

BUT, the 1st one is the XP boot.ini, should'nt this one be changed to give the ubuntu priority instead of the XP?.

Somehow in my ignorance it seems it is this last ine
  
        "...C:\wubildr.mbr = "Ubuntu" ....."

that should move up somewhere & whichever is the Windows line take its place, and these be done within Windows, does this makes sence:- 
 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

---

### Post by nichos on 2011-07-31
Thanx aussiebean,

I truly apologise if I doubled it but, the first time I asked this question within another subject post I made, & when there was no answer I took it that that post expired & should start a new one for this quiry, then came an answer saying :-

"......The best I can suggest for now is that you ask this question in the 'Mint4Win' forum - viewforum.php?f=159...."

I'll endeaver not to repeat it.         .......nick

---

### Post by snoopo71 on 2011-08-04
You're using wubi, I've never used it and I think I can't help you. Try to read about the wubi start. Sorry.

---

### Post by bcbc on 2011-08-04
Right click My Computer, Properties, Advanced tab, Startup & Recovery settings, select Ubuntu from the drop down list for default OS. Don't modify the timeout on this page (you can lower it, but I wouldn't go less than 15). The reason for this is that some people set it to 0 and then you can't boot XP anymore (it's easy to fix in XP as you can modify the boot.ini, but you need a recovery prompt in vista/7).

I believe, in the next release, Wubi will suppress the grub menu (second menu) so you just see the windows boot manager. But for now, you'll have to live with both being displayed.

If you want to use Ubuntu more than Windows, you might consider [migrating]("http://ubuntuforums.org/showthread.php?t=1519354") or installing direct.

---

### Post by nichos on 2011-08-05
SOLVED

Thanks all for your paitence & help.

I understood by now that I do not have enough knowledge to deal with this.

Will stay with present bootloader & each time catch it to select ubuntu.

---

