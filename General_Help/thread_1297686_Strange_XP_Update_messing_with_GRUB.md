---
title: "Strange XP Update messing with GRUB?"
date: 2009-10-22
forum: General Help
---

### Post by Cornova on 2009-10-22
About an hour ago I sat down on XP and noticed the security/software update icon on the tray. I updated as usual and as asked to restart so I did. I have a dual boot system with XP on one hard drive and Ubuntu on the other.

When I rebooted, it was giving me:
```
GRUB LOADING stage 1.5
Error 18
```

After rebooting over and over I finally got to see the GRUB list with Ubuntu+recovery and XP, however when I clicked on them I got various errors.

When selecting XP from GRUB:
```

Error 29: Disk write error

```

When selecting Ubuntu 9.04, Kernel 2.6.28-11-generic:
```

Error 16: Inconsistent filesystem structure

```

When selecting Ubuntu 9.04, Kernel 2.6.28-11-generic (Recovery):
```

Error 18: Selected cylinder exceeds maximum supported by BIOS

```

After awhile restarting continuously I ended up with the same "Error 18" message and no others regardless of which OS I chose.

So I shut my PC down and went next door to do a quick search at the neighbors because I immediately suspected the XP update messed with the BIOS or something eventhough I couldn't find anything in the BIOS settings. I came back for my tea real quick and turned on my PC real fast and then all the sudden it booted all the way in XP.

I am now afraid to restart my PC (lol). Is anyone else having a similar problem after an update?

---

### Post by P4man on 2009-10-22
sounds like you got a problem with the harddrive where grub is installed. Id suspect a hardware error rather than a windows update issue here. Having the machine off for a while might have allowed it cool and work again for a short time.

Where did you put grub? is it on the mbr of the ubuntu drive and pointing to /boot on the ubuntu drive, or did you put it on the mbr of the windows drive pointing to /boot on the ubuntu drive? 

If you put it on the ubuntu drive, and left the windows drive intact you could always boot straight in to windows by disconnecting the ubuntu drive or changing the boot order in the bios.

If you did it the other way around, then booting either windows or ubuntu requires **both** drives to be working intially. 

Anyway, my guess is there is problem with the harddisk on which you have ubuntu, and which is needed briefly during boot for grub. Id suggest disconnecting the ubuntu drive, boot from a windows cd and run fixmbr and fixboot to install windows bootloader on the windows drive. Then install grub on the second drive (disconnect the windows drive to be sure). That way either OS can boot without needing the other. You can manually add windows to the grub menu and set your bios to boot the second drive, so by default you get a choice. And in case of trouble you can boot one or the other.

---

### Post by Cornova on 2009-10-22
I always edited GRUB in Ubuntu so it's on that drive. Thanks for the reply.

Come to think of it, the XP drive is loud and is sometimes just incredibly sluggish in performance. For example, when I first boot up and launch Firefox, it takes like 40 seconds just to open. This is after it boots, not immediately after the desktop pops up. The slow program thing happens to certain folders and other apps as well. I've been moving files to the Ubuntu drive expecting it to die one of these days.

---

### Post by P4man on 2009-10-22
> **Cornova said:**
> I always edited GRUB in Ubuntu so it's on that drive. Thanks for the reply.

Your /boot/grub folder is no doubt on the ubuntu drive, but stage1 on the master boot record may not be. Easy to find out, disconnect the ubuntu drive. If windows boots up, then you have grub entirely on the ubuntu drive and windows still has its own bootloader. That'd be good. If it gives a grub error, then you installed grub on the mbr of the windows drive, which I suspect. Meaning you need both disks to have a bootable system.

---

### Post by Cornova on 2009-10-22
> **P4man said:**
> Your /boot/grub folder is no doubt on the ubuntu drive, but stage1 on the master boot record may not be. Easy to find out, disconnect the ubuntu drive. If windows boots up, then you have grub entirely on the ubuntu drive and windows still has its own bootloader. That'd be good. If it gives a grub error, then you installed grub on the mbr of the windows drive, which I suspect. Meaning you need both disks to have a bootable system.

I'll test this out tomorrow, thanks!

---

### Post by Cornova on 2009-10-22
It looks like the problem is the XP drive. I unplugged the Ubuntu drive and got the error 18 message. I then reversed it and Ubuntu booted right up with XP unplugged. Plugged XP back in and after restarting over and over again finally it allowed me to boot into XP. The HD may be close to failing or something so I am backing up everything I need to.

---

