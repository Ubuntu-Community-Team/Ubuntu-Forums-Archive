---
title: "Clashing Grub And Windows Boot Loader"
date: 2009-07-28
forum: General Help
---

### Post by Tanner2007 on 2009-07-28
So I reinstalled my windows vista, shortly after reinstalled the RC version of windows 7, then soon after installed a 64 bit ubuntu

now In grub during boot only gives me 3 choices, ubuntu, recovery ubuntu mode, and windows vista (minus mem test)

but wheres my windows 7? so I tried to manuly edit my menu.lst file for windows 7, i failed....

now heres where I think it goes wrong, when I click on windows (loader) selection during the boot on grub, soon after i click on it....it loads windows boot loader then choose are vista or windows 7

so pretty much is like this

-booting up
-grub tells me to choose my ubuntu partition or windows (Loader)
-once I select windows (loader) 
-It takes me to windows MBR and ask me to choose win 7 or vista

so how could i erase my windows boot loader, and have grub be able to have win 7 as a selection of Os to choose from?

```


title Ubuntu 9.04, kernel 2.6.28-13-generic
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=9feeba0c-f0eb-4bc5-a949-764acdb38e8c ro xforcevesa quiet splash vga=792
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=9feeba0c-f0eb-4bc5-a949-764acdb38e8c ro xforcevesa  single
initrd /boot/initrd.img-2.6.28-13-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista
root (hd0,0)
chainloader +1
savedefault
makeactive

```

I tryed adding win 7 my self and putting
root (hd0,1) all the way to root (hd0,3)
and get error 12, but I loaded both windows OS in windows MBR record so im guessing I need to erase windows MBR and use grub for it all can someone tell me how?

---

### Post by merlinus on 2009-07-28
If you search on this problem, you will find that running two versions of windows leads to this situation.  In other words, whichever version grub loads will bring up the windows bootloader, and you can choose which one from that.

Easybcd, a windows program, will let you select from however many versions you have installed and linux.

---

### Post by Tanner2007 on 2009-07-28
> **merlinus said:**
> If you search on this problem, you will find that running two versions of windows leads to this situation.  In other words, whichever version grub loads will bring up the windows bootloader, and you can choose which one from that.

Easybcd, a windows program, will let you select from however many versions you have installed and linux.

I have tried that program once, all it did was mess me up more, do you know what to search for or another to have grub be able to load ubuntu,win vista and win 7 without having windows boot loader at all? i tried to erase win MBR and messed up my pc and had to restore my grub but even then got same error

---

### Post by merlinus on 2009-07-28
Again, grub cannot load more than one version of windows because if you have more than one version of same, whichever one you choose will always bring up the windows bootloader.

Sue billy-boy, if you do not like this.  Or better yet, run windows in a VM.

---

### Post by theozzlives on 2009-07-28
Should be able to add Windows 7 to grub, just follow the example set in menu.lst (different partition though. As far as the Vista boot menu, go to start > run > msconfig, choose the boot tab and edit your boot.ini. THIS IS NOT FOR NOVICES! You can foul up your system if your not careful.

example:

title Windows 7
root (hd0,1)
chainloader +1
savedefault
makeactive

BACKUP your menu.lst and boot.ini before attempting this.

---

### Post by Tanner2007 on 2009-07-28
I have it once like that, grub offered vista and win 7 without editing anything, but I tried to edit menu.lst, and choose about 4 (hd?,?) and none would work.......And tryed removing the windows mbr and only grub, and then windows vista menu.lst was not changed but did not load anymore, so how can i do this without having to edit boot.ini, i dont want to jack things up

---

