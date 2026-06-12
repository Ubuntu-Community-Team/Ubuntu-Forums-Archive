---
title: "Dariks Boot &amp; Nuke on USB Flash disks"
date: 2009-12-11
forum: General Help
---

### Post by Greg Xix on 2009-12-11
I know that many of us here use the Linux-based, Dariks Boot and Nuke for wiping their HardDrives. A few days ago I decided/realized that 2 of my USB Flash disks needed this service as well. And was happy to see that the regular DBAN version can do those as well.

My question is. What would the appropriate wipe method for a USB Flash vs a HDD?

I used the DBAN DoD 5220-22.M, 7 passes on one of the disks today(took about 40 mins).

But is that overkill?

Or would a DoD Short, 3 pass be more appropriate for these little guys?

Also, how much am I wearing out the Flash Disk's life but doing these?

---

### Post by lykwydchykyn on 2009-12-11
If I cared about the life of the disk, I'd overwrite it once with zeros and let it be.  If I was getting rid of the disk, I'd smash it with a hammer and be done with it.

---

### Post by JBAlaska on 2009-12-11
Well on my thumb drive with the meaning of life on it...I did use DoD 5220-22.M. but for simple stuff like drawings and sketches of UFO occupants and non-human reports, I just put it in a solar furnace at 3,000 °C for 15 min or until golden brown.. Then, no can defend..

---

### Post by bodhi.zazen on 2009-12-11
> **lykwydchykyn said:**
> If I cared about the life of the disk, I'd overwrite it once with zeros and let it be.  If I was getting rid of the disk, I'd smash it with a hammer and be done with it.

+1 in terms of overwriting the data with zeros once

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

use dd to do this :

```
dd if=/dev/zero of=/dev/sdxy
```where /dev/sdxy is your flash drive.

---

