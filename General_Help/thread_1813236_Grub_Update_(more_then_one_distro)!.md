---
title: "Grub Update (more then one distro)!"
date: 2011-07-27
forum: General Help
---

### Post by EgoGratis on 2011-07-27
If u have more than one Linux distro installed on PC only one of them updates Grub (2)? Is this correct? 

How do you deal with this? When distro that doesn't control Grub gets new kernel and it doesn't update Grub menu do you always have to go in the distro that controls Grub and update Grub or is there a better way of updating Grub when more then one Linux distro are installed on the same system?

---

### Post by oldfred on 2011-07-27
Yes you have to update your other install so its grub.cfg is current, then reboot into the install that is in the MBR and run update-grub to find the new entry.

There are some work arounds if you want to manually edit 40_custom to directly boot another install.

If your other install is Debian based, it puts links in / (root) to the most current kernel. You then can boot from the link that is always current.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by EgoGratis on 2011-07-27
I see. I would have to modify Grub (2) to boot directly from the partition and automatically select the newest kernel? Then updating Grub (2) is not needed any more.

Only drawback is losing the possibility to boot older kernel if never won't boot?

---

### Post by oldfred on 2011-07-27
There also is the old link. It only has two versions, and the old link will always be the previous. (.old on end of vmlinuz & initrd links).

You can also create your own entry for an old kernel in 40_custom, if you want to save that kernel. Just copy from grub.cfg before turning off os-prober. But I house clean older kernels periodically and only keep the two most current anyway.

---

