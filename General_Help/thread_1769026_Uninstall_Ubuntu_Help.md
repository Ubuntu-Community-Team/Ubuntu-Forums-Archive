---
title: "Uninstall Ubuntu Help"
date: 2011-05-27
forum: General Help
---

### Post by Jaket25 on 2011-05-27
Hi there, a while ago I installed Ubuntu 10.10, and ever since I've just not physically used it as software on Windows isn't available on Ubuntu.

So I thought as it's using quite a bit of memory space that I'll remove it.
I've heard of some problems when people try to remove it, so I'd like a detailed guide.

I installed Ubuntu 10.10 on a USB stick.
I also can't seem to get internet on Ubuntu as my internet card drivers are messed up with it.

If anyone can run me through this with a step by step guide (has to be for a newbie) I'd be incredibly grateful.

Thanks :)

---

### Post by LordNeo on 2011-05-27
Boot from the USB and then open the Disk Utility.
Check your disk and remove the logical partition containing Ubuntu (without touching your NTFS partition holding Windows nor the small partition (100mb) that Windows 7 creates (if you have W7 of course).

After that, reboot using a Windows disk, and from the recovery console type "fixmbr" and that's it.

---

### Post by Jaket25 on 2011-05-27
I'm running off of Vista (Pre-installed).

---

### Post by LordNeo on 2011-05-27
First Boot in Windows Vista and try to use fixmbr from command line.
Then reboot and check that grub doesn't show up (if you installed it using Wubi, it's a whole other world).
If this step is ok, then from Windows (or a Live Linux CD) remove the Ubuntu partitions (it should be only a logical partition 2 slices).

---

### Post by Jaket25 on 2011-05-27
> **LordNeo said:**
> First Boot in Windows Vista and try to use fixmbr from command line.
Then reboot and check that grub doesn't show up (if you installed it using Wubi, it's a whole other world).
If this step is ok, then from Windows (or a Live Linux CD) remove the Ubuntu partitions (it should be only a logical partition 2 slices).

Like I said, I'm a newbie and have no idea.
How do I get to fixmbr?

And I installed Ubuntu 10.10 from the Universal USB creator thing.

Need a more detailed and well explained guide :confused:

---

### Post by LordNeo on 2011-05-27
(This should be explained from a MS guy xD)
Boot into Windows Vista, then open a command prompt (cmd in the search bar and press enter)
then in the black window with the white letters type:

fixmbr

Press enter
Then it will do some magic tricks and continue.
Now reboot, it should boot directly into Windows Vista without showing you the GRUB selection screen (where you can decide to boot into Ubuntu or Windows Vista)

When you are done with that use any disk utility (fdisk, Gparted for Windows or google for a partition utility) and delete the partition with Ubuntu (it will be clear wich one it is, because will be the only "logical" partition).

That's all, sorry if i can't explain it better, but disk partition in Windows is not as simple as in Linux

---

### Post by bcbc on 2011-05-27
If you installed with Wubi you can uninstall from Control Panel--> "Uninstall a program" (look for the Ubuntu entry).

If you did not use Wubi, you will need to boot from a Windows repair CD or Install DVD. Boot to the repair prompt and replace the bootloader in the drive MBR with the command:
```
bootrec /fixmbr
```

Then make sure that the computer boots direcly into windows before using the Windows Disk Manager to delete or reformat the partition you used for Ubuntu.

If you're still not sure, then post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") or the output of 
```
sudo fdisk -l
```

---

