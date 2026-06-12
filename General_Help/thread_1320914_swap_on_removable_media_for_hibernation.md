---
title: "swap on removable media for hibernation?"
date: 2009-11-09
forum: General Help
---

### Post by fowie on 2009-11-09
My acer timeline 3810t has an SSD and 4GB of ram, so I decided not to worry about installing a swap partition.  Of course, having no swap partition means I cannot hibernate.  I would like to hibernate, but perhaps use removable media instead of the SSD, since the laptop has a build in SD slot that I never use.  I formatted my 2GB SSD card into linux-swap, and swap-on worked fine, so did hibernate.  However, coming out of hibernate, ubuntu starts up brand new, as if it didn't see the hibernated image on the SD card.  Is it possible to use an SD card for hibernate-able swap?  What do I need to change in my fstab or elsewhere so that it re-loads the image from the SD card on wake?

---

