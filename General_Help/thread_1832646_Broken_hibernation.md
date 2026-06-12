---
title: "Broken hibernation"
date: 2011-08-25
forum: General Help
---

### Post by Lockheed on 2011-08-25
The system is Arch 64 and their forum is sometimes useless with things not covered in wiki. I've been trying to set it up for long time but to no avail.

I am using  uswsusp/hiber script rather than pm-utils because
1. I think pm-utils cannot suspend to file
2. I get further with  uswsusp

But further doesn't mean to the end.

menu.lst
```
title  Arch
root   (hd0,1)
kernel /vmlinuz26 root=/dev/sda3 resume=/dev/sda3 resume_offset=1748992 ro quiet vga=785
initrd /kernel26.img
```

 /etc/suspend.conf
```
resume device = /dev/sda3
resume offset = 1748992
#snapshot device = /dev/snapshot
#resume device = /dev/sda8
#image size = 350000000
#suspend loglevel = 2
#compute checksum = y
compress = y
#encrypt = y
#early writeout = y
#splash = y
shutdown method = shutdown

```

/etc/hibernate/hibernate.conf
```
TryMethod ususpend-disk.conf
TryMethod tuxonice.conf
TryMethod disk.conf
TryMethod ram.conf
```


Now, if I run **hibernate -F /etc/hibernate/ususpend-disk.conf** this is what happens:
1. s2disk: snapshotting system
2. % goes to 100% and laptop shuts down

If I know press the power button to resume laptop:
1. Comp boots up, arch starts resume
2. I can see this on screen
```
_
_ (the lower one is blinking)
```
3. beep
4. everything goes blank

At this point, I need to hold power button for 10 seconds to poweroff laptop.

Help appreciated.

---

### Post by prshah on 2011-08-25
> **Lockheed said:**
> 
kernel /vmlinuz26 root=/dev/sda3 resume=/dev/sda3 resume_offset=1748992 ro quiet vga=785

[s]The resume  partition is not correct. It has to point to your swap partition. Please post back if you want more information on this.[/s]

Re-read everything; sorry, this advice is not valid.

---

### Post by Lockheed on 2011-08-25
I do not have swap partition. I am using swap file as per [this entry]("https://wiki.archlinux.org/index.php/Swap#Swap_file_creation").

---

