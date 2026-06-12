---
title: "Upgrading Using Live CD"
date: 2009-08-16
forum: General Help
---

### Post by Nate Shoffner on 2009-08-16
I would just like to know this for future reference.  When Karmic Koala comes out.  Will I be able to upgrade from Jaunty by using the Live CD or is there more to it than that?  Thank you.

---

### Post by Bucky Ball on 2009-08-16
It is always much quicker and less error prone to just install the next version on the partition you have your current install.

---

### Post by Nate Shoffner on 2009-08-16
Yes, that's what I plan on doing.  I'm just wondering if there are any risks while doing it.  I would of course back up all my data before I would attempt it.

---

### Post by prshah on 2009-08-16
> **Nate Shoffner said:**
> When Karmic Koala comes out.  Will I be able to upgrade from Jaunty by using the Live CD 

You can update from the "alternate" CD, not the live CD.

This is what I have done every time since Gutsy.

---

### Post by Nate Shoffner on 2009-08-16
Feel kinda dumb for asking, but what is an alternative CD?

---

### Post by Bucky Ball on 2009-08-16
The alternate cd is the text based installer (as opposed to the desktop which involves colourful graphics and GUIs).

Not quite sure what previous poster means; you can upgrade from inside Ubuntu without using a CD (which I think is what you did anyhow). Upgrading from a CD means you would have put the new version on a CD, booted from it and simply re-installed that way (rather than delete and add new packages to what you have).

---

### Post by prshah on 2009-08-17
> **Nate Shoffner said:**
> Feel kinda dumb for asking, but what is an alternative CD?

An "alternate" CD is a install CD that does not contain the "live" interface. It can be downloaded from the same place from wherever you downloaded your "live" CD.

The alternate CD is used in cases where your system has less memory, or a non-VESA compliant display card, for an OEM install, any other situation where the live CD does not work for any reason, and/or upgrading.

I prefer downloading the alternate CD to perform upgrades, rather than download them over the Internet, because I often find the repositories comparatively slow. It is also a lot better when I have multiple machines to upgrade.

I suggest you download the alternate CD (don't use torrents; there are usually very few seeders for alternate CD images), then upgrade with it (just pop it in the CDDRIVE and click upgrade when prompted) and after completing the install, check for updates.

You can also manually mount the ISO image, rather than burn it to a CD; post back if you want details on this.

---

### Post by tperwez on 2009-08-26
> **prshah said:**
> 

You can also manually mount the ISO image, rather than burn it to a CD; post back if you want details on this.

I am also interested in using either the Alternate CD or the ISO image. I have just one concern. My desktop computer actually has wireless network; it is just not reliable enough to do distro upgrade. Would there be any problem in doing distro upgrade by ISO image (or Alternate CD) for a machine that does have network connection? For example, will all the sources lists etc be maintained to notify of the updates online? I perform such updates fairly frequently over the network.

Also I would appreciate if you could provide the details on using the ISO image for upgrade. Thanks. Best regards.

---

### Post by prshah on 2009-08-27
> **tperwez said:**
> Would there be any problem in doing distro upgrade by ISO image (or Alternate CD) for a machine that does have network connection? 

you could provide the details on using the ISO image for upgrade

I have always upgraded using the alternate CD image because I have to upgrade multiple machines.

There is no problem in upgrading from the CD even on a machine that is connected to the Internet. 

However, CD images are out-of-date almost as soon as they are downloaded. In this case, the installer uses the newer files it finds on the Internet rather than those on the CD, which effectively means it upgrades from the Internet. So, you should disable Internet (unplug, switch off) and then upgrade the distro.

At the end of the upgrade, everything will be the same whether you upgrade from the CD or the Internet; sources, etc. No problems either way. However, once the CD upgrade is finished, you will also have to check for updates.

To mount the ISO image, use the command ```
sudo mount -o loop image.iso /mnt -o defaults,ro
``` The CD will then be available in "/mnt" (or whatever mount point you choose). In the root of the CD will be a shell script cdromupgrade(.sh) which can be run directly.

---

