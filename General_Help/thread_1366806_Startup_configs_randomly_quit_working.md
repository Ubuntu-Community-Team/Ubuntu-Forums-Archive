---
title: "Startup configs randomly quit working"
date: 2009-12-28
forum: General Help
---

### Post by mclark1129 on 2009-12-28
Hello,

Lately I've been having some trouble with start up configurations that previously worked all of a sudden quit working.

First is the timeout setting on my Grub2 configuration, it was set at 3 seconds and was working great, now when the grub menu appears the timeout is disabled and you must choose a selection to continue.  Here are the contents of my /etc/default/grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```I'm using a custom script to generate my menu items, and I've disabled the default scripts that automatically detect your installed OS's

Here are the contents of that file:

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fc5629cc5629888a
    chainloader +1
}

menuentry "Ubuntu" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2606999c-d421-44d7-a09a-e41820622f5f
    linux    /vmlinuz root=UUID=2606999c-d421-44d7-a09a-e41820622f5f ro   quiet splash
    initrd    /initrd.img
}

menuentry "Ubuntu (Recovery Mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2606999c-d421-44d7-a09a-e41820622f5f
    linux    /vmlinuz root=UUID=2606999c-d421-44d7-a09a-e41820622f5f ro single 
    initrd    /initrd.img
}
```The other problem I'm having relates to setting up my wireless connection on startup.  I'm using a script I wrote in my /etc/init.d called setup-wireless.  Again, it worked perfectly until one day my wireless connection was no longer being set up.  If I run the script manually after I log in it works great.  Here is that script just in case:

```

#! /bin/sh
# This script disables the ssb module and enables the wl module for
# wireless networking.


modprobe lib80211
insmod /lib/modules/`uname -r`/kernel/net/wireless/wl.ko

```I think I *may* have applied an update to Ubuntu when prompted a week or so ago, but I don't know if the began occurring before or after the update.

If anyone has any clue on what might have gone wrong, I'd really appreciate the insight.

Thanks,

Mike

---

### Post by dcstar on 2009-12-28
> **mclark1129 said:**
> Hello,

Lately I've been having some trouble with start up configurations that previously worked all of a sudden quit working.

First is the timeout setting on my Grub2 configuration, it was set at 3 seconds and was working great, now when the grub menu appears the timeout is disabled and you must choose a selection to continue.
.........

[http://ubuntuforums.org/showthread.php?p=8573983](http://ubuntuforums.org/showthread.php?p=8573983)

---

### Post by mclark1129 on 2010-01-04
David,

I think I've been able to figure out that both of the problems I've posted are related to Karmic's use of upstart in place of System V init scripts.  I've found that when I run 'runlevel' the output is 'unknown'.  If I run 'init 2' to set the system at runlevel 2, then my wireless script is executed and if I am to reboot, then the GRUB screen once again has a timer.  Of course, since the system boots into runlevel unknown the timer once again disappears.  

Now what's left to figure out is how to get the system to either go into a valid runlevel that doesn't conflict with upstart, or GRUB just may need to be updated to work properly with systems that use upstart.

Mike

---

