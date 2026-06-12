---
title: "Ubuntu took over my computer?"
date: 2010-11-12
forum: General Help
---

### Post by isaacbeans on 2010-11-12
Hi, I recently installed ubuntu 10.10 its all fine and dandy, but  I did not think I would need windows again so I deleted windows complete off my Dell NV 52 laptop. I went to install windows again and then dual boot ubuntu by installing it again later but once my window cd finished installing, and rebooted, it went to a black screen that said grub bootloader or something like that and said file system not recognized. I proceeded to use many live cds to completly reformat my hard drive, but the grub bootloader is not being deleted and proceeds to stay on my laptop. Ubuntu is an amazing OS, But Ubuntu has never done this in previous versions. So I did not take precautions to do it carefully. So can anyone assist me, sorry for my carelessness for letting this happen.

---

### Post by lmarmisa on 2010-11-12
Maybe the Windows installer did not update the code area of the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of your hard drive and the GRUB loader is still there.

Try this procedure: boot your system from an Ubuntu live CD, open a terminal and type this command:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```

The previous command writes the code area of the MBR with the loader of Windows XP, deleting completely the GRUB loader.

Now, reboot the computer (remove the Live CD) and check if Windows is able to start up (you will have a chance if you installed XP; no chance in case of Vista or W7).

If the system is not recovered after this procedure, try to reinstall Windows.

---

### Post by wilee-nilee on 2010-11-12
It would help to actually see what on the hard drive. boot a live Ubuntu cd and click on the bootscript in my signature and down load it run the command on the link page to generate a new file. Open a reply in your thread click on the # to create code tags and paste the text from the generated file in between.

---

