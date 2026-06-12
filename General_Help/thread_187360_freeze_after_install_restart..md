---
title: "freeze after install restart."
date: 2006-06-02
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-02
hey all, I actually managed to get ubuntu to install, but now, on the restart, it seems to be froze at 'Waiting for root file system...' there must be some solution.....

---

### Post by Patrick-Ruff on 2006-06-02
ok well it just did something different, after an extended wait time, it gave me the following screen 
```

       Booting 'Ubuntu, kernel 2.6.15-22-386
root     (hd0,0)
   Filesystem tiype is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-23-386 root=dev/sda1 ro quiet splash root=
             [Linux-bzImage, setup=0xc1c00, size=0x15774d]
initrd /boot/initrd.img-2.6.15-23-386
             [Linux-initrd @ 0x1f916000, 0x6ad37f bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
    No volume groups fiound
ALERT! does not exist.  Dropping to a shelL!



BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#   

```

and I can enter text.

---

### Post by Patrick-Ruff on 2006-06-02
can someone PLEASE answer!!! I can't figure this out, I have no idea whatsoever what to do...and nobody is bloody answering, out of all these active users, no answers whatsoever...please, PLEASE help!

---

### Post by bobbymcsteels on 2006-06-03
havin same problem and has happened a couple of times and had to reinstall cos I dont know what to do.... anyone know what to do to fix this?

---

### Post by Bionic_Beefpile on 2006-06-05
I'm having the same problem.  I upgraded from Breezy to Dapper, and get stuck at "waiting for root file system".  I tried running "evms_activate", but that dumped out with errors.

I can run Dapper using an older Kernel (2.6.12-10-686), but now my WiFi is acting up.  I assume this is some sort of kernel issue (maybe having to do with my SATA HDD), but I'm having trouble nailing down a cause.

---

