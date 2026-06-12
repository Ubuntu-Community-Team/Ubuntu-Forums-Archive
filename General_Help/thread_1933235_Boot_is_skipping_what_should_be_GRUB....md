---
title: "Boot is skipping what should be GRUB..."
date: 2012-02-28
forum: General Help
---

### Post by sean09 on 2012-02-28
I had an install of Ubuntu 10.04 on my PC, and just today partitioned some of the empty space and installed Windows 7 to it. Now, I've gone from Windows 7 to installing Ubuntu more times than I could count, but I've never gone from Ubuntu alone to installing Windows 7.

Now when I boot my PC, it goes straight to Windows 7, instead of giving me a choice for which OS to boot into.

I've searched but haven't found anything substantial. At the moment, I am unable to access my Ubuntu 10.04 install, but this new install of Windows 7 is running fine.

Anyone have any solutions?

---

### Post by efflandt on 2012-02-28
Windows overwrote grub2 in the mbr of the drive with its mbr which knows nothing about your Ubuntu.

See [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by sean09 on 2012-02-28
> **efflandt said:**
> Windows overwrote grub2 in the mbr of the drive with its mbr which knows nothing about your Ubuntu.

See [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

Described my problem perfectly, thanks a lot. :D

I'll be sure to try this fix as soon as possible and report back with results if something goes wrong.

Appreciate the help, mate.

---

### Post by sean09 on 2012-02-29
Following the steps above, I booted to a LiveCD of Ubuntu 10.04, and installed Boot Repair. However, when I run Boot Repair, it goes through the motions for the first handful of steps (mounting, checking OS, etc), but then when it gets to "Scanning systems.", it stays there forever.

Does this typically take a very very long time (especially in comparison with the other steps, which all took a few seconds at most)?

---

### Post by oldfred on 2012-02-29
If scanning hangs up, it may mean a file issue on one of the partitions, so it cannot mount it.

You can try directly running the boot info script. git version has some fixes, so run it. Then we may be able to suggest fixes.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

