---
title: "Multiple entries show up in Natty GRUB"
date: 2011-06-24
forum: General Help
---

### Post by jamadagni on 2011-06-24
Hello. I installed Natty on my two laptops and for some reasons I additionally installed Maverick on one Laptop and Lucid on the other both alongside the Natty installations on separate partitions.

Note that the GRUB is Natty GRUB only, I chose not to install GRUB when doing the Maverick/Lucid installs.

What happens is that on both laptops the Natty GRUB os-prober churns out four or five entries for the older Ubuntu installation. Please find attached a copy of my grub.cfg. I have to manually edit /boot/grub/grub.cfg to remove the superfluous entries. 

Why is this problem? Is there a fix?

---

### Post by Quackers on 2011-06-24
You can delete the older kernels if you don't need them any more through synaptic package manager. Just enter the kernel number into the search box and mark them for complete removal. (Three entries for each kernel).
Don't remove the latest though!
Then run sudo update grub in your controlling grub installation to update the menu.

---

### Post by jamadagni on 2011-06-25
Hello. Perhaps you did not understand my problem. I am not complaining about multiple kernels being installed *on* Natty. I perfectly understand that when the same installation has many kernels all those kernels will be listed (under "Previous Linux Versions" on Natty) but that is not what I am talking about. 

I am saying that when there is a Maverick or Lucid installation *alongside* Natty, (NOTE, separate installation) and boot/GRUB control is with Natty, the GRUB menu created by Natty has multiple entries for the Maverick or Lucid installation. Please see the grub.cfg I attached.

---

### Post by Quackers on 2011-06-25
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jamadagni on 2011-06-25
Please find compressed RESULTS.txt attached and advise. Thank you.

---

### Post by oldfred on 2011-06-25
Since you already have a 40_custom, you may not want to use the easy way - grub customizer

I turn off os-prober and add my own entries in 40_custom.

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Ubuntu puts into / (root) a link to the most current kernel, so we boot from the link to always get the latest update.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

I like to add a spacer or two also:

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

---

