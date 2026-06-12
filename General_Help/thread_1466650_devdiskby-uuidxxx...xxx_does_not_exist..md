---
title: "/dev/disk/by-uuid/xxx...xxx does not exist."
date: 2010-04-30
forum: General Help
---

### Post by elmoosecapitan on 2010-04-30
hey all,


While running my browser I did not realize that my computer was not plugged into the wall. when i rebooted the thing I got the following:
```

(initramfs) gave up waiting for root device. common problems:
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait for the right device)
- missing modules  (cat /proc/modules; ls /dev)
alert! /dev/disk/by-uuid/ca49e8ad-6538-4f61-a88c-577ce3bc5440 does not exist. dropping to a shell.

busybox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

```

i had a similar problem before before i upgraded to 9.10 and I was about to correct it without using a live disk or doing a fresh install but i do not remember how to do it. any suggestions on what I should do?

---

### Post by dino99 on 2010-04-30
dont worry, if you ask it to do a task reaching the web without plugin it, it try and complaint, normal dont you ? :confused:

it should have logged some info i guess, but first reboot and you will see.

---

### Post by elmoosecapitan on 2010-04-30
I am sorry, but what?

---

### Post by elmoosecapitan on 2010-04-30
rebooting with a recovery kernel I get this:

begin: waiting for root file system... ...
[2.340358] usb 3-2: configuration #1 chosen from 1 choice
done.
gave up waiting for root device....

---

### Post by dino99 on 2010-04-30
> **elmoosecapitan said:**
> I am sorry, but what?

what ? is it working fine now after rebooting ?

are you running Lucid or else ?

---

### Post by elmoosecapitan on 2010-04-30
I am running 9.10 and I am still having problems.

---

### Post by elmoosecapitan on 2010-04-30
let rephrase:

after rebooting i get the same error in the same place.

---

### Post by Charlietje on 2010-04-30
when you go into the grub, don't boot your system but choose to edit the boot option

On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY" with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.


and then boot from the edited grub line

once you have booted succesfully, you need to change your grub menu  so the system doesn't check for uuid but for /dev instead

---

### Post by bomber991 on 2010-05-01
I think I'm getting a similar error.  Right now I just type in exit, and then Ubuntu will continue to boot, but there's gotta be a way to fix it.  Probably by getting rid of the UUID thing like Charlie said.

---

