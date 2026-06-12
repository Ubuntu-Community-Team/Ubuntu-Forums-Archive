---
title: "Grub2 problems"
date: 2010-01-01
forum: General Help
---

### Post by kornfan71 on 2010-01-01
Hi,
So, I'm using a multi-boot system: Windows XP, Windows 7, and a few Linux distros, including Ubuntu 9.10. I have Grub2 installed (managed by Ubuntu 9.10), and I've been having some issues booting Windows 7. Finally, I found out how to get it correct in my case.

This is my custom menu entry from /etc/grub.d/11_Other_OS
```
menuentry "Windows BOOTMGR" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3c288bc7288b7ea0
    drivemap -s (hd1) ${root}
    chainloader +1
}
```I've tested this command, and it works, but there is a small problem. After running "update-grub," ${root} is not in grub.cfg...
The line becomes: drivemap -s (hd1)
Obviously this is not the correct command. If I append ${root} to the line, then boot that command list, all is well.

How can I get "${root}" to 'transfer' to grub.cfg after running "update-grub"?

UPDATE:
I just found out that the above command list only works for booting Windows 7. Windows XP immediately reboots if this command is used to chainload BOOTMGR.
This command does work for Windows XP, but not for Windows 7.
```

    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3c288bc7288b7ea0
    drivemap -s (hd1) (hd0)
    chainloader +1

```So, any ideas on how to merge these 2 commands together so both WinXP and Win7 boot from it? I'd hate to have to use 2 Grub entries to get to the same bootloader....
Thanks in advance.

---

### Post by Leppie on 2010-01-01
does grub2 not detect the os's automatically?
what's the result of these commands:
```
$sudo grub-install --recheck /dev/sda
$sudo update-grub
```

---

### Post by kornfan71 on 2010-01-01
Grub does detect it automatically, but seeing as I have Kubuntu and Gentoo also installed, I prefer to use my own configuration. (That involves loading the configfiles for Kubuntu and Gentoo, and chainloading Windows BOOTMGR.)

I went ahead and ran the commands you gave me, and I got 2 entries for Windows 7. (One of them was randomly installed by Windows 7, but it doesn't use it....)
The entry loads BOOTMGR correctly, and from there Windows 7 boots properly. Trying to boot Windows XP still results in a reboot. Nothing appears on the screen before the reboot.

It would seem that to boot XP, the drive must be mapped to hd0, but doing so compromises Windows 7, unless the ${root} variable is used, which, since life is never easy, compromises Windows XP. It was simple to get XP and 7 working with Legacy GRUB. Why is Grub2 so picky???

---

### Post by Leppie on 2010-01-01
if you installed 7 after xp without setting the new 7 partition to be bootable, 7 took over xp's boot loader.
in order to boot xp, you now will have to chainload into the 7 menu and boot xp from there.

---

### Post by kornfan71 on 2010-01-01
I guess I needed to be more clear. That is what I'm doing. I installed 7 after XP, so now I have 2 entries in BOOTMGR: Win7, and XP, which just loads NTLDR.
So, what I was trying to say is loading XP from 7's bootloader fails unless I use the command "drivemap -s (hd0) (hd1)", which in turn causes 7 to fail.

Gotta love Windows...

---

### Post by Leppie on 2010-01-01
you could try to make everything boot from grub2...
have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1150729").

basically, you have to restore the xp boot loader with the xp cd.
then rebuild the 7 boot sector using [this tuturial]("http://ubuntuforums.org/showpost.php?p=5726832").

---

### Post by kornfan71 on 2010-01-01
Alright, I'll try all of this out and get back to you. *crosses fingers*

---

### Post by kornfan71 on 2010-01-01
Thanks!
Windows 7 and XP each are booting with their own bootloaders and entries in GRUB, which is, IMO, much cleaner than going GRUB > BOOTMGR > NTLDR > XP....

The only issue now is something I'll take care of elsewhere....Windows 7 is using the boot screen from Vista (ugly green scrolling bar) instead of the pretty new Win7 screen.
No big deal.

Again, thanks! :guitar:

---

### Post by Leppie on 2010-01-01
Glad it's working :)

found this article on 7 boot splash screen issue:
[http://www.mydigitallife.info/2009/02/19/fix-and-restore-windows-7-boot-screen-that-changes-to-vista-style/](http://www.mydigitallife.info/2009/02/19/fix-and-restore-windows-7-boot-screen-that-changes-to-vista-style/)

hope this helps.

---

