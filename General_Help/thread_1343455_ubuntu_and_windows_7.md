---
title: "ubuntu and windows 7"
date: 2009-12-01
forum: General Help
---

### Post by chuckman45 on 2009-12-01
this is my system.
 
Microsoft Windows 7 Ultimate
Version 6.1.7600 
System Manufacturer ECS
System Model GeForce6100PM-M2
System Type X86-based PC
Processor AMD Athlon(tm) 64 X2 Dual Core Processor 4600+, 2400 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date Phoenix Technologies, LTD 6.00 PG, 2/2/2009
SMBIOS Version 2.4
Windows Directory C:\Windows
System Directory C:\Windows\system32
Boot Device \Device\HarddiskVolume1
Locale canada
Hardware Abstraction Layer Version = "6.1.7600.16399"
User Name WIN-9CZ3SRU1AD6\Administrator
Time Zone Atlantic Standard Time
Installed Physical Memory (RAM) 2.00 GB
Total Physical Memory 1.87 GB
Available Physical Memory 1.28 GB
Total Virtual Memory 3.75 GB
Available Virtual Memory 2.80 GB
Page File Space 1.87 GB
Page File C:\pagefile.sys
 
i'm trying to get ubuntu 9.10 to install so i can duel boot. but it will not install.
when i put the cd in the drive and restart. it starts with 2 lines of linux then shuts the computer off. i even tried this in windows and nothing. any help

---

### Post by ssulaco on 2009-12-01
Could have a bad image
Check hashes?
Burn at the slowest speed possible

---

### Post by chuckman45 on 2009-12-01
[SIZE=5][COLOR=#000000]ssulaco i checked the hash and its ok.[/COLOR][/SIZE]
[SIZE=5]burn the iso at 2 speed.[/SIZE]
[SIZE=5][/SIZE] 
[SIZE=5]put the cd in drive rebooted when it came on it asked for language. then i clicked on check cd. it shut down computer.[/SIZE]

---

### Post by ssulaco on 2009-12-01
Try Imgburn...it has the option to "verify" the burn
[http://www.imgburn.com/](http://www.imgburn.com/)
and a different disk,Ive occasionally had "new" disks that were bad.
can you run ubuntu "live" on this computer?....if not do you have another computer to try it on?
If you can run it live,and the ubuntu desktop appears try installing it by clicking on "install ubuntu" icon
I still think you have a bad burn if you cant run it live.

---

### Post by Elep.Repu on 2009-12-02
I use blindwrite.

---

### Post by OrangeCrate on 2009-12-02
> **chuckman45 said:**
> this is my system.
 
Microsoft Windows 7 Ultimate
Version 6.1.7600 
System Manufacturer ECS
System Model GeForce6100PM-M2
System Type X86-based PC
Processor AMD Athlon(tm) 64 X2 Dual Core Processor 4600+, 2400 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date Phoenix Technologies, LTD 6.00 PG, 2/2/2009
SMBIOS Version 2.4
Windows Directory C:\Windows
System Directory C:\Windows\system32
Boot Device \Device\HarddiskVolume1
Locale canada
Hardware Abstraction Layer Version = "6.1.7600.16399"
User Name WIN-9CZ3SRU1AD6\Administrator
Time Zone Atlantic Standard Time
Installed Physical Memory (RAM) 2.00 GB
Total Physical Memory 1.87 GB
Available Physical Memory 1.28 GB
Total Virtual Memory 3.75 GB
Available Virtual Memory 2.80 GB
Page File Space 1.87 GB
Page File C:\pagefile.sys
 
**i'm trying to get ubuntu 9.10 to install so i can duel boot. but it will not install.**
when i put the cd in the drive and restart. it starts with 2 lines of linux then shuts the computer off. i even tried this in windows and nothing. any help

Did you partition the hard drive to make room for a Linux installation? If not, see post #11 in this thread for guidance:

[http://ubuntuforums.org/showthread.php?t=1343235&page=2](http://ubuntuforums.org/showthread.php?t=1343235&page=2)

---

### Post by jamesofthedead on 2009-12-02
Im not sure what your problem is, but I do know that W7 overrides GRUB. I upgraded from Vista and am unable to boot Ubuntu.

---

### Post by ST3ALTHPSYCH0 on 2009-12-02
> **jamesofthedead said:**
> Im not sure what your problem is, but I do know that W7 overrides GRUB. I upgraded from Vista and am unable to boot Ubuntu.

You can reinstall Grub, but that's an issue for another thread.

@ OP

Try your Ubuntu disc in another machine to verify that it is working. If it causes the same problems then you know the disc is bad.

---

