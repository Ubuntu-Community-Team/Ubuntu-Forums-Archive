---
title: "Strange errors"
date: 2010-08-08
forum: General Help
---

### Post by kuzimoto on 2010-08-08
How it happens:
I get home after a long trip(couple months), away from the computer. I dualboot windows xp and ubuntu 10.04, so I select ubuntu in the bootloader and after getting some strange messages I reboot and try again, still no luck. I try an ubuntu 10.04 cd that I just burned (I know it works because I tried it on 2 other computers), and all it did was hang on the loading screen forever.

I don't remember everything I did, but after a few live cds here I am now:
deleted grub/reset mbr to only work for windows.
deleted Ubuntu - not formatted exactly, just deleted the data.
can't access any live cds.

Error Messages:
Error message I get while trying to start up the Ubuntu 10.04 CD.
```

BusyBox v1.13.3 (Ubuntu 1:1.12.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live filesystem

```
This is a message I get after selecting "start ubuntu without any modifications to your computer" on an ubuntu 9.10 CD.
```

/init: line 1: can't open /dev/sr0: no medium found
mount: mounting /dev/sr1 on /cdrom failed: Invalid argument
stdin: error 0
/init: line 1: can't open /dev/sr0: no medium found
/init: line 1: can't open /dev/sr0: no medium found
mount: mounting /dev/sr1 on /cdrom failed: Invalid argument
stdin: error 0
/init: line 1: can't open /dev/sr0: no medium found
/init: line 1: can't open /dev/sr0: no medium found
mount: mounting /dev/sr1 on /cdrom failed: Invalid argument
stdin: error 0


BusyBox v1.13.3 (Ubuntu 1:1.13.3-wubuntu7) built-in shell (ash)
Enter 'help' for a list of buit-in commands.

(initramfs) unable to find a medium containing a live file system

```
Tried running gparted but all i got were some more strange error messages.

I'm really not sure what to do at this point.

---

