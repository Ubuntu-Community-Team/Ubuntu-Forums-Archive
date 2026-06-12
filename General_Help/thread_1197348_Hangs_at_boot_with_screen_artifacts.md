---
title: "Hangs at boot with screen artifacts"
date: 2009-06-26
forum: General Help
---

### Post by b.bailey on 2009-06-26
I've been happily using 9.04 since it came out but the other day I accidentally selected recovery mode in the grub boot loader. I let it do it's thing and resumed the boot without any recovery options. Ever since then, it loads the progress bar to completion but right when it turns the screen off to switch to the log in resolution, it flashes the completed progress bar back with changed colors, multiple tiles of it, sometimes slowly eliminating tiles until there are two strange-colored progress bar tiles. 

I've tried fsck, dpkg, and xfix. All to no avail.

---

### Post by prshah on 2009-06-26
> **b.bailey said:**
> 
the other day I accidentally selected recovery mode

switch to the log in resolution, it flashes the completed progress bar back with changed colors, 

Can you put a (approximate) date/time to "the other day"? And can you please post the output of```
ls -l /etc/X11/xorg*
```

This will list previous configuration files for X (the GUI). See if you have a matching configuration file for the approx date/time you accidentally recovery booted, and then copy that file over the present config file; then reboot and see if it works.

Eg```

sudo cp -p /etc/X11/xorg.conf.**20090413134916** /etc/X11/xorg.conf
``` will copy over the xorg.conf file that was overwritten on 2009-April-13-at-13:49:16 to the current xorg.conf file.

Post back with output details if this is too confusing.

---

### Post by b.bailey on 2009-06-26
I believe it was around the 16th or the 18th.

Should I be doing this from the recovery shell? The output is as follows:

> /etc/X11/xorg.conf
/etc/X11/xorg.conf.20090616200246
/etc/X11/xorg.conf.20090616212348
/etc/X11/xorg.conf.20090618222432
/etc/X11/xorg.conf.20090625221456
/etc/X11/xorg.conf.conf.dis-upgrade-200905121803
/etc/X11/xorg.conf.failsafeI tried copying the files as you've suggested, 

> cp -p /etc/X11/xorg.conf.20090616200246 /etc/X11/xorg.confand everything seems to be back to normal now. Thanks a bunch!

---

### Post by prshah on 2009-06-26
> **b.bailey said:**
> 
I tried copying the files as you've suggested, 
cp -p /etc/X11/xorg.conf.20090616200246 /etc/X11/xorg.conf 

and everything seems to be back to normal now.

Just a small note; the copy command needs to be preceeded by sudo; ie "sudo cp..."

Good to know it's working fine.

---

