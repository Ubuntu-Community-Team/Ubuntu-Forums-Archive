---
title: "Grub destroyed and noboot from CD possible"
date: 2011-10-27
forum: General Help
---

### Post by Huygenz on 2011-10-27
Hello Ubuntus!

I'm really stuck.
Yesterday I wiped out my etx3-partition with Windows, because I wanted a fresh install of Ubuntu.

I know, that Grub is deleted this way and won't work.
But I intended to install from a Live-CD as done before.

I didn't quite finish yesterday so the Laptop (Lenovo G560) went to hibernate.
This morning I wanted to start up, to re-install Ubuntu from CD.

To my surprise suddenly I can't enter BIOS anymore. And I can't change the boot-order to boot directly from CD.

So now I'm stuck atz the Grub Rescue Shell,with nothing to use.
It keeps saying "Incorrect Filesystem", even if I try a FAT32 formatted USB-Stick (it shows up in Grub's ls-command as "hd1"). I "see" the stick, but don't know how to handle it.

I just removed my harddrive. This enables me at last to boot a live-CD but this doesn't really help as I can not fix my hdd mbr with that.

So everything is stuck:
- Grub starts only to Grub Rescue
- Can not boot from CD (live-CD or Windows Rescue to fix mbr)
- Can not Boot from HDD as the mbr is pointing to a wiped partition
- Can not Access USB-Stick to repair Grub
- Can boot from Live-CD but without HDD.

My idea was to get Grub on the USB stick and use grub rescue to point it there to get a grub boot menu.
Is this possible?
Or is there a better way to recover this?

Help would be MUCH appreciated, thank you in advance.

---

### Post by collisionystm on 2011-10-27
> **Huygenz said:**
> Hello Ubuntus!

I'm really stuck.
Yesterday I wiped out my etx3-partition with Windows, because I wanted a fresh install of Ubuntu.

I know, that Grub is deleted this way and won't work.
But I intended to install from a Live-CD as done before.

I didn't quite finish yesterday so the Laptop (Lenovo G560) went to hibernate.
This morning I wanted to start up, to re-install Ubuntu from CD.

To my surprise suddenly I can't enter BIOS anymore. And I can't change the boot-order to boot directly from CD.

So now I'm stuck atz the Grub Rescue Shell,with nothing to use.
It keeps saying "Incorrect Filesystem", even if I try a FAT32 formatted USB-Stick (it shows up in Grub's ls-command as "hd1"). I "see" the stick, but don't know how to handle it.

I just removed my harddrive. This enables me at last to boot a live-CD but this doesn't really help as I can not fix my hdd mbr with that.

So everything is stuck:
- Grub starts only to Grub Rescue
- Can not boot from CD (live-CD or Windows Rescue to fix mbr)
- Can not Boot from HDD as the mbr is pointing to a wiped partition
- Can not Access USB-Stick to repair Grub
- Can boot from Live-CD but without HDD.

My idea was to get Grub on the USB stick and use grub rescue to point it there to get a grub boot menu.
Is this possible?
Or is there a better way to recover this?

Help would be MUCH appreciated, thank you in advance.

Is it a SATA drive?

If its SATA you can plug it in while the computer is running from the live cd and it will be recognized. Just like a USB drive. I do this all the time.

---

### Post by Mark Phelps on 2011-10-27
Don't know how your hard drive plugs into your laptop.  I've seen everything from bays (in which the drive is easily inserted and removed) to fragile tiny ribbon cables -- that area easy to break.

If yours is easily insertable such that there's no risk of damage, then you could try connecting it after you're running in Ubuntu.

If it were my laptop, I would try to get Windows booting first, since I was going to reinstall Ubuntu anyway.  I would also use a USB-to-Hard-Drive adapter to connect the drive to the laptop.

Since you probably don't have any kind of Windows Repair CD, the link below is to a Boot Repair CD that claims to be able to repair Windows MBRs as well:  

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Once you boot with this CD, you could connect the drive via the adapter cable and see if it can rewrite the MBR.

---

### Post by Huygenz on 2011-10-27
Thank you both. Got it fixed with your help! THANKS A LOT!

Anyways, had a little breath-taker here:
After hotplugging the HDD (I considered the plug-port as "reliable") the screen went black.

Oh noes!

But after hard-reset the Bios-Options shown up again, so I was able to boot from CD with my HDD plugged. MBR is fixed now via Windows Rescue Disk and Win7 boots up propperly.

Don't know why the Bios was inaccessible, must be a known bug with Lenovo-Lapstops (found something about that).

So hotplugging helped me.
Good work guys and thanks A LOT again! You made me happy. :popcorn:

---

