---
title: "Trying Ubuntu Server via USB on Headless"
date: 2011-08-18
forum: General Help
---

### Post by EricAtUNC on 2011-08-18
Hi,

I have an HP MSS 487 (headless).  I was going to update to WHS2011 but was thinking of trying Ubuntu Server first.  My MSS has a USB slot, but I'm not sure how to start and run Ubuntu Server from that USB stick.  I can use remote desktop to access the box.  Any ideas?

I'll also need to install something on my other pcs/macs so that I can get the backups working.  I didn't see anything that is similar to the whs connector software (client).  Would I need to install a full Ubuntu client to do the backups?

Thanks for any help.

---

### Post by CrusaderAD on 2011-08-18
Are you trying to boot to a USB stick running the LAMP server? That shouldn't be too tough. Just install the ISO to the USB stick and boot to it. As far as configuring backups, check this out... [http://www.geekgrid.com/?p=19]("http://www.geekgrid.com/?p=19")

---

### Post by seawolf167 on 2011-08-18
For the usb booting, take a look at [UNetBootin]("http://unetbootin.sourceforge.net/"). As for the backups, you have a lot of [options]("https://help.ubuntu.com/community/BackupYourSystem"), though I prefer *rsync*. You can mount a network share (as in your other computers) and use [rsync ]("https://help.ubuntu.com/community/rsync")to keep backups.

---

### Post by EricAtUNC on 2011-08-19
I'm assuming I can't use remote desktop to remote into the server once I have ubuntu server running on the usb stick.  Is there another program I can use for this?

---

### Post by EricAtUNC on 2011-08-19
Nevermind, I found another thread that explains my options.

---

