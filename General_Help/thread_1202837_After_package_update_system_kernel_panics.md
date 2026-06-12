---
title: "After package update system kernel panics"
date: 2009-07-02
forum: General Help
---

### Post by ThaddeusW on 2009-07-02
This one has me stumped. Today my notification said there were some new updates, so I go ahead and start the updates. There was also a new kernel available (2.6.24-24-generic) so I figured why not and installed the new kernel. I am running Ubuntu 8.04 btw.

After I rebooted my startup screen locked up and the keyboard lights were flashing, oh no a KERNEL PANIC. So I reboot and hit escape and select the recovery mode which gives me verbose output. Well this is what is causing the kernel panic:

```

ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/init: .: 1: Cant open /tmp/net-eth0.conf
[    30.343584] kernel panic - not syncing: Attempted to kill init!

```

So at first the new kernel was suspect. Could be a bug I thought so I booted from an Ubuntu 8.04 live CD, mounted everything and chrooted into my disk. I then mounted boot and installed my previous 2.6.24-18-generic kernel which installed just fine. So I reboot and AGAIN I am presented with the same lockup. I then start the recovery mode for 2.6.24-18 and again the same kernel panic message pops up involving networking.

My next step was to ensure that the boot partition had no errors or bad blocks. I ran both fsck and badblocks on the boot partition and both show no errors. So now I feel like I am at a dead end :(

Any ideas on what happened? I though it could be a hardware problem but if the Ubuntu live CD boots fine and networking works then what gives? Another tidbit of info is the live CD did kernel panic once but it did not give enough info on what caused it. But other than that it has booted five times since with no problems.

A few months ago I upgraded the hard disk so I still have the older install on a 40 gig disk. I will try to see if that disk boots with no errors. I will report back with my findings.

---

### Post by scrooge_74 on 2009-07-02
I would have tried the other kernels in the grub list before installing any kernels from the Live CD. Sorry can't help beside bumping this thread

---

### Post by ThaddeusW on 2009-07-03
FIXED!

I figured out my problem and thought I would share it with everyone.

After I posted I shutdown and connected the hard drive to another system and attempted to boot it. Well instead of the kernel panicking it kept looping trying to find an NFS file system to mount. Bingo!

It turns out that when I was fooling with PXE booting I was putting together a initramfs that mounts a root nfs file system. In order to do that I had to change the boot parameter in my /etc/initramfs-tools/initramfs.conf from local to nfs. I forgot to change it back to local so when the new kernel was installed it created an iniramfs that was trying to mount an nfs root. For some reason it would kernel panic on this system but the other system it partially worked and was trying to look for the nfs root.

The solution was to use the live cd to mount the disk up and then bind /dev to the mounted directory and chroot into it. I then mounted /boot, changed the flag in the initramfs.conf file to local, uninstalled both of the kernels and then reinstalled one to test it. Rebooted and it now works.

Lesson learned. I am glad I could fix it myself without resorting to reinstalling.

---

### Post by aesis05401 on 2009-07-03
> **ThaddeusW said:**
> FIXED!


Thanks for posting the resolution.  I learned something from your explanation.

---

