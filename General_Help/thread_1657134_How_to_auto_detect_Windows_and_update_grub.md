---
title: "How to auto detect Windows and update grub?"
date: 2010-12-31
forum: General Help
---

### Post by Externalist on 2010-12-31
What I've tried so far :

sudo update-grub

This only updates menu.lst but since Ubuntu 10.10 doesn't use menu.lst anymore, it seemed pointless. I've been looking into /boot/grub/grub.cfg but I'm not sure exactly what I have to do. It would be nice if there was a way to automatically detect windows on my harddrive and update grub accordingly. If there is no automatic way, the I'm all welcome with any help on manual editing. Just for the record, windows is on a different HDD than the one ubuntu is on.

---

### Post by drs305 on 2010-12-31
> **Externalist said:**
> What I've tried so far :

sudo update-grub

This only updates menu.lst but since Ubuntu 10.10 doesn't use menu.lst anymore, it seemed pointless. I've been looking into /boot/grub/grub.cfg but I'm not sure exactly what I have to do. It would be nice if there was a way to automatically detect windows on my harddrive and update grub accordingly. If there is no automatic way, the I'm all welcome with any help on manual editing. Just for the record, windows is on a different HDD than the one ubuntu is on.

If you run the boot info script and post the contents of RESULTS.txt we can see what is happening with your boot files. You can download the script from the following link. You can run it from any Linux OS or from the LiveCD.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

There is now plenty of information about Grub2, including the links in my signature line. The "G2-Basics" provides a fairly comprehensive introduction to Grub2. G2-Tasks shows how to accomplish the normal tasks a user would want to perform with the G2 bootloader.

---

### Post by Externalist on 2010-12-31
I looked into GRUB2 common tasks, then Hermans site and found the magic command.

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

This worked liked a charm. :) Reboot. Done!
Thanks, and Happy New Year!

---

### Post by drs305 on 2011-01-01
Glad you were able to get your system working correctly. :-)

For future reference:

In Grub2, the command 'update-grub' is a stub for 'grub-mkconfig -o /boot/grub/grub.cfg'; i.e. it is a shortcut for the longer command. The 'update-grub' command was carried over from Grub legacy. 

What this means in your case is that G2 has not completely taken over your system and you have a combination of Grub 2 and Grub legacy. Should you have a problem with your bootloader in the future, I would suggest you purge Grub legacy (grub) and reinstall Grub 2 (grub-pc).

Here is guide for doing this. If you are still able to boot normally, use only Steps 2-5 of the 'chroot' procedure to purge/reinstall. There is no need to actually 'chroot'. If your bootloader fails and you have to boot a LiveCD, use the full 'chroot' procedure (starting at Step 1).
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

