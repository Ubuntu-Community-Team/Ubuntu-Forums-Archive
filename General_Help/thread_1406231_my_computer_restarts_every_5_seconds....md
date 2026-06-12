---
title: "my computer restarts every 5 seconds..."
date: 2010-02-13
forum: General Help
---

### Post by august north on 2010-02-13
okay guys, this is what's up. About two weeks ago I installed ubuntu 9.10 desktop with a dualboot to my windows 7, which was already on there. everything went fine, but I couldn't configure my wireless to work, so after a few days I gave it a rest and basically forgot about; I just stuck with windows. anyways, yesterday night I installed a program called solidworks on my system. I woke up this morning, turned on my computer, and this is what happened-
 
it turns on for about 5 seconds, but when it hits "grub loading", after about half a second it restarts. it's basically an infinite loop, until i throw in a cd or hit f8, but I don't know what to do with either of those options, so I'm kind of stuck.
 
I'm posting this in the ubuntu forums because I have NO idea what's wrong with it, and no idea of where to start. I'm hoping that someone can give me a little advice. I've got both installation disks, but I don't know what to do when I put them in. I'm no neo anderson, so please, if you have any ideas, i dont care how bad, throw them out there. I've got an intel pentium 4 processor, and like i said, i've got a dualboot with windows 7 and ubuntu 9.10. 
 
okay, lets do it.

---

### Post by NightwishFan on 2010-02-13
If you do not have Ubuntu, then simply reinstall windows bootloader from Windows Recovery CD. I am not sure how.

If you have Ubuntu still, then go into Ubuntu and run:
```
sudo update-grub
```

If nothing will boot, you can use the super grub disk.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by BigG123 on 2010-02-13
Uninstall Grub and Ubuntu and start over.
Boot up with the windows cd and select repair then command prompt and type
```

bootrec.exe /fixboot

```

Then reboot and make sure windows boots with no Grub loader.  Then install Ubuntu making sure to delete old Ubuntu partitions and make a new / partation and swap partititons.

---

### Post by august north on 2010-02-13
thanks for the replies, guys. but how can i delete ubuntu if I can't get into windows. I'm looking for instructions on how to boot from the installation disk (yes, i'm that dumb), but if you read this and i haven't written are reply yet, I haven't figured it out...

---

### Post by 2hot6ft2 on 2010-02-13
If the windows 7 is a bootleg there are problems with the Windows 7 boot loaders being used resulting in the system rebooting. See the long thread here:
[Program-based-Windows-7-loader]("http://forums.mydigitallife.info/threads/8632-Program-based-Windows-7-loader")
Might take a look at pages 572 and up.

Sometimes you can get in by holding a key down during the boot like the Ctrl, Esc, or Shift for examples. Then if you go into safe mode first you can reboot into normal mode.

If you have a licensed copy you can put the disc in as soon as you can get the drive open (which should be as soon as there's power before the grub, just keep pushing the button to open the drive) and boot to it and choose recovery and choose the fix boot option.

Also cd/dvd drives have a small hole in the front to manually open the drive. The power doesn't even have to be on. Just straighten a paper clip and push it straight into the hole once you feel it stop give it a little push and the drive will pop open. Then you can put your disc in and turn it on.

---

### Post by august north on 2010-02-13
so I ended up following this tutorial:
 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
 
and that made windows my primary boot thingy again. i'm logging on right now. thanks for the help, really. peace.
 
-august

---

