---
title: "Can I hibernate ubuntu (dual boot)"
date: 2011-09-19
forum: General Help
---

### Post by alexthepenguin on 2011-09-19
I have a dual boot set up (windows 7 and ubuntu). Can I hibernate ubuntu in this setting? I tried that in ubuntu yesterday but it seems that my computer couldn't wake up from hibernation...

---

### Post by Mark Phelps on 2011-09-20
HOW did you install Ubuntu? IF you installed it via Wubi, I believe that hibernation is NOT supported for Wubi installs.

---

### Post by sanderd17 on 2011-09-20
It's also dangerous to hibernate Ubuntu and start Windows afterwards, and more dangerous the other way around.

You can even lose files this way.

---

### Post by bcbc on 2011-09-20
Ubuntu will usually refuse to mount a hibernated windows partition unless you force it. So it's safe to hibernate windows and then boot Ubuntu. (Note it's not possible to start Wubi if you hibernated Windows).

As Mark Phelps said, Wubi does not support hibernation. And often a normal dual boot (when letting the installer decide) will fail to provide the necessary size swap partition for hibernation. You need at least the size of your RAM - and then a little more for overflow.

---

### Post by SecretCode on 2011-09-20
You definitely can hibernate Ubuntu and resume it with a Windows 7 partition on the disk. 

But (1) there can be issues with booting the other OS when one is hibernated, as other poster have pointed out and (2) some motherboards/BIOSes are not well supported out of the box by Ubuntu power management and can have problems with hibernate and suspend - but this is nothing to do with dual boot.

---

### Post by alexthepenguin on 2011-09-20
Hi thanks for all your replies. No I'm not using wubi. But after I hibernate ubuntu I can't start it again (I didn't try booting windows in between). any thoughts?

---

### Post by sanderd17 on 2011-09-21
If secretcode sais some BIOS don't support Ubuntu very well, you could try to boot Ubuntu with the "acpi_osi=" option (without arguments).

That makes the BIOS forget about the 'fixes' it has to do to get Vista working. See my signature on setting boot options for better information.

It's only a guess, certainly no guarantee it will work.

---

### Post by SecretCode on 2011-09-21
You might also need to try with **pcie_aspm=off**

And/or you might need **resume=/dev/sda5** where sda5 is your swap partition.

---

### Post by bcbc on 2011-09-21
Check out your /var/log/syslog and look for messages prefixed with "PM:"

i.e.
```
cat /var/log/syslog | grep PM:
```

Check your swap partition size using:
```
free
```

The memory must be < swap.

Also search on or post your computer specs as it's likely that someone else has found the same issue.

Other things:
```
sudo blkid     #shows the uuid of the swap partition
```

Check it's the same as here:
```
cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume
```

---

