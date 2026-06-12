---
title: "Broken: Ubuntu installed on secondary hdd"
date: 2006-04-16
forum: General Help
---

### Post by zuccs on 2006-04-16
hey,

I setup ubuntu 5.10 on a hard drive that was set to secondary (when there was nothing set as primary and pressed F1 in DOS to resume loading from secondary). This works fine as long as the hard drive is still set to secondary. Now I want to change the hard drive so it is set to primary (and use another hard drive as a secondary hdd).

But when I set the ubuntu hard drive to primary hard drive, I get an error along the lines of the following when booting up (not the actual error I get but close enough :P):

```

ALERT! /dev/hdb does not exist. Dropping to a shell!

Busybox v1.00=pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off.
```

Now I need to change this so Ubuntu will boot from the same hard drive but when it is set to primary. Any ideas?

Thanks in advance

---

### Post by Ramses de Norre on 2006-04-16
In grub you'll need to change your root partition so that it's set to the bootable partition of the first instead of the second hd, you can set these values in /boot/grub/menu.lst.
To do so, press esc after bios screen to get grub menu, select your kernel but instead of enter press e (I think it's e, you can check at the bottom of your screen) to edit the kernel line, then find the line starting with "kernel" and change the setting root=/dev/hdb to root=/dev/hda
When booted succesfully apply the change to be permanent in menu.lst.

---

### Post by zuccs on 2006-04-16
thanks man, that worked perfectly. i knew it would be pretty simple, but I have only been using ubuntu for a couple of days...

another quick one for you ;) ...with my new secondary hdd, how can i format it using FAT? In XP it only gives me the option of NTFS, in both control panel and using XP installation CD. Can I format the second hdd thru linux (or windows?!) as FAT so i can read/write data to it. I do not need an installation of windows/linux on it. Thanks mate

---

### Post by Ramses de Norre on 2006-04-16
Gparted can perfectely format drives in FAT, but some people have problems with fat partitions made by gparted that aren't readable in windows..
In windows click start > run type compmgmt.msc
Then choose disk management, you can create partitions there and it should be possible to use fat.
I don't know why nor when those problems with gparted's fat partitions occur..

---

### Post by zuccs on 2006-04-16
yeh, i went to that disk management in XP (via control panel though), and it only gives me the option of NTFS. It's a fairly new 80GB hard drive, so I don't see why I cannot format as FAT. I might have to try gparted then, although the whole idea of setting up this secondary data hard drive was so I could transfer to windows if i needed to.

---

### Post by plors on 2006-04-16
[QUOTE=Ramses de Norre]Gparted can perfectely format drives in FAT, but some people have problems with fat partitions made by gparted that aren't readable in windows..
<snip
I don't know why nor when those problems with gparted's fat partitions occur..[/QUOTE]

That's because the gparted on ubuntu's livecd is way too old :)
This issue has been solved in gparted for a long time now. Just go to [http://gparted.sourceforge.net]("http://gparted.sourceforge.net") to download the latest version.

have fun :)

---

