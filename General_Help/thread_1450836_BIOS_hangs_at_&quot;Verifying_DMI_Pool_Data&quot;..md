---
title: "BIOS hangs at &quot;Verifying DMI Pool Data&quot;..."
date: 2010-04-09
forum: General Help
---

### Post by lespaul_rentals on 2010-04-09
Hey everyone,

My command-line Ubuntu Server 8.04 install spontaneously rebooted overnight.  I'm not sure why (haven't had time to fully investigate the logs or whatnot).

I couldn't connect to the SSH server or Apache, so I turned on the monitor and noticed the BIOS was hanging at "Verifying DMI Pool Data."

There are three HDD in the system, 2 IDE and 1 SATA.  I ended up installing Ubuntu on the SATA drive, which Ubuntu sees as /dev/sdc.  My system initially could not boot until I told BIOS to use a different drive as the primary boot device.  However, it's been a couple months now with no problems.

Here's what changed: I mounted one of my IDE drives (both were unused up to this point) in order to download torrents to it.  The system saw it as /dev/sda.  I added a partition to it, formatted it, etc.  I then configured fstab to mount the drive at boot time.  Finally, I mounted it manually.  Everything seemed to go through fine; I even downloaded a torrent to it.

I'm just wondering if anyone has experienced anything similar to this before.  I'm not behind my computer right now, and I'm sure this will be easy enough to fix once I add GRUB to the MBR of the sda device.

Anyone know if there's an easier way?

---

