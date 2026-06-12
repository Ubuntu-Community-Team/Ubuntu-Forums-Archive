---
title: "how can i save the verbose boot process ?"
date: 2010-06-06
forum: General Help
---

### Post by dino99 on 2010-06-06
Fighting against Grub2 boot troubles, i've seen on screen that the problems comes when detecting internal SATA devices.

But logs dont help about the scanning boot process, so i search a way to log this verbose process by adding some code into /etc/default/grub or something else.

All ideas are welcome as i want to report this problem

---

### Post by sdennie on 2010-06-06
If you are having boot problems caused by SATA issues, I'm not sure how you could log them.  If the errors are coming up so early in the boot process that the disks haven't been mounted yet, there is no place to write a log file.

---

### Post by dino99 on 2010-06-06
> **sdennie said:**
> If you are having boot problems caused by SATA issues, I'm not sure how you could log them.  If the errors are coming up so early in the boot process that the disks haven't been mounted yet, there is no place to write a log file.

yes of course disks are not mounted yet, but i guess these comments can stay in a ram file then writen on disk when mounted, or is setting a debug parameter on boot line could add more info into logs ?

---

### Post by dino99 on 2010-06-07
have found a way to go ahead:

[http://v3.sk/~lkundrak/grub2-gdb/howto.html](http://v3.sk/~lkundrak/grub2-gdb/howto.html)

not so easy and its a outdated doc

---

### Post by dino99 on 2010-06-07
i've filled a bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/590727](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/590727)

---

### Post by nemilar on 2010-06-07
Are you looking for the dmesg?

Try looking at the contents of /var/log/dmesg -- I think that is what you are asking for.

```
cat /var/log/dmesg | less
```

---

### Post by Lampi on 2010-06-07
@dino: you mentioned using AHCI - does this run with P-ATA drive? I'd consider switching BIOS to IDE-only in case sth is messed up with with your drive detection.

---

