---
title: "Pandaboard will not boot - problem with / and /tmp"
date: 2012-05-02
forum: General Help
---

### Post by evolvd on 2012-05-02
I followed these instructions:
> Linux

Steps:

Place the SD card at your host computer.
Make sure the SD card is not mounted (just umount it if needed)
Identify the correct raw device name (like /dev/sde - not /dev/sde1)

Run the following command to write it:
(replacing omap4 and sde with the right values i.e. just omap for a beagle image.)

zcat ./ubuntu-12.04-preinstalled-desktop-armhf+omap4.img.gz |sudo dd bs=4M of=/dev/sde ; sudo sync

Found [https://wiki.ubuntu.com/ARM/OmapDesktopInstall]("https://wiki.ubuntu.com/ARM/OmapDesktopInstall")

It looks like everything is going ok, a message comes up saying the card is being resized, goes down for a reboot and when it comes back up I get the following message:

> Errors were found while checking the disk drive for /

Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery

For example if I press "S" to skip I get another error message that reads:

> The disk drive for /tmp is not ready yet or not present

If I don't do anything for a few minutes I get to a console screen that says:

> Ubuntu 12.04 LTS Localhost.localdomain tty1

localhost login:

I don't know what the login would be fore this.

I can get into manual recovery but from there I have no idea what to do as I'm not sure what is going on. Since I'm using a pre built image I thought this would just work?

Any ideas on this?

---

### Post by evolvd on 2012-05-03
a little bump for a little help

---

### Post by masterdew on 2012-11-15
Bump!

Followed same instructions, getting the same error.

---

