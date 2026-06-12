---
title: "Dual boot, GRUB &amp; updating Master Boot Record"
date: 2010-07-09
forum: General Help
---

### Post by cmcesq on 2010-07-09
I'm running a dual boot config using GRUB for the boot menu.  I have WinXP on one hard drive and Ubuntu on a separate drive.  

I'm the only one who uses Ubuntu and the family wants me to upgrade from WinXP to Win 7.   In order to do so I will have to do a complete install of Win 7, which will wipe-out my Master Boot Record and (I suspect) completely screw-up my dual boot set-up making it impossible for me to get back to Ubuntu.  

I assume there's some way to get it back so I won't also have to completely reinstall Ubuntu.

Help?

Many thanks in advance.

---

### Post by Woody1987 on 2010-07-09
It will wipe the MBR, but grub can be easily reinstalled, look here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Go to the section: Reinstalling from livecd

---

### Post by spydeyrch on 2010-07-09
Well, it depends on how you installed them.

Did you install XP first, then disconnect the drive and then install ubuntu on the second drive?

Or was the XP drive still connected when you installed ubuntu?

The way that I have my multi-boot system (Win7 Pro, Mint9, Ubuntu 10.04) set up is as follows, but with a few extra steps taken out because it is a triple boot and not a dual boot:

-1TB -> HDD #1
-500GB - > HDD #2

--------------------------
-HDD1 connected, no others.
-Install Win 7 to HDD1 drive.
-After install completes, disconnect HDD1.
-Connect HDD2
-Install Ubuntu10.04 to HDD2
-After install completes, connect other HDD
-Via BIOS, select either HDD2 as primary drive to boot from.
-Boot into primary drive (HDD2 selected previously in the BIOS)
-Once you are logged in, in the terminal run:
```

sudo update-grub2

```This will add the other OS (Win7) to that HDD2's grub boot menu.

What this does is keep Grub on it's own drive and not mess with the Win7 drive's MBR. So, you can remove the Linux HDD (HDD2) or the Win7 HDD (HDD1) and the other will still boot w/out any issues. Plus you can add other drives, change the drive order (as in where they are physically connected to the motherboard (I think only for SATA)), and as long as your Linux HDD is the primary boot drive, all you have to do is boot into linux and run that command from above and viola!, reboot and then you have the other drive's OS available in the Grub boot menu.

This is what I would recommend in for future installs, if you ever do a future install from scratch (fresh install).

---------------

As far as your current issue, I would recommend that you: 

-Disconnect your linux HDD from the machine. (you can leave it in the machine but just disconnect the power and/or data cable)
-Install Win7 to the XP HDD.
-After installation is complete, disconnect your Win7 HDD.
-Re-connect the Linux HDD and make sure it is the only HDD connected.
-Follow Woody1987's advice about re-installing GRUB but if possible, re-install it to your Linux HDD via the live cd/usb.
-Once successful, restart the machine to make sure it worked.
-Once confirmed successful, shutdown the machine.
-Re-connect the Win7 HDD.
-Make sure that, via the BIOS, you boot from the Linux HDD.
-Once booted into Linux run that code from above:
```

sudo update-grub2

```-once done, restart machine and you should have access to both win7 and ubuntu with the ability to take out one or the other drive and still boot the remaining drive. 

----

Hopefully that isn't too much info and/or too confusing. I have done this with a triple boot machine several tiems and it has always worked. BUT I always started it out this way. I never had to re-install grub via a live cd/usb.

-Spydey:)

---

