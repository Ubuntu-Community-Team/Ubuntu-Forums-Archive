---
title: "root parition now unallocated space"
date: 2011-01-16
forum: General Help
---

### Post by Nexhis on 2011-01-16
Hi: 

I have a 1TB drive and divided it for a dual boot setup; win XP SP3 on one half and ubuntu on the other. Upon rebooting one day, I received the 'error no such partiiton' and found myself at the grub rescue prompt. I tried to repair grub, reinstall grub, fsck to check the filesystem but the root partition was listed as unallocated space and could not be mounted. Nothing worked; I checked the HDD for errors, etc and everything was clean. Windows also saw the parition as free space then unallocated space. The swap partition was still present and unaffected. Does anyone have any ideas or have seen this before?
Thanks in advance

---

### Post by Quackers on 2011-01-16
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Nexhis on 2011-01-17
I apologize as I failed to mention that I ended up reinstalling ubuntu about a day after and am back up and running with the same setup. So far so good, the initial installation was only about 1-2 days old so I didn't have any data files. I was just wondering if anyone knew a general reason or had seen that before?

---

### Post by dabl on 2011-01-17
The failure of Grub to boot the Linux OS suggests a Grub issue, for example if there was an update of relevant grub-pc related files, but update-grub didn't complete correctly, or something like that.

However, if a booted Live CD, with GParted running, indicated that the partition was actually unallocated space, then that's an entirely different issue.  That would suggest that somehow the partition table on the hard drive was corrupted, and lost the partition information.  That's a bad thing -- you should keep an eye on that hard drive, and keep your data backed up (and it doesn't matter how new the drive is).

---

