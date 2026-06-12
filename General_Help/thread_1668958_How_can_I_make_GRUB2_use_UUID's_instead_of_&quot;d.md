---
title: "How can I make GRUB2 use UUID's instead of &quot;/dev/...&quot;?"
date: 2011-01-17
forum: General Help
---

### Post by TheOnlyMrK on 2011-01-17
I'm installing Ubuntu 10.04.1 to my flash drive as I speak (had to wipe it out in a rare case that I needed the extra ~5GB it was using to hold some important info) and the last time it was installed GRUB2 wouldn't work right because it would use stuff like "/dev/sda1" instead of UUIDs so whenever it was used in any other computer it would fail to boot, I never took the time to properly fix it and just did a search and replace in all of the GRUB2 configuration files for "/dev/sda1" to be replaced with the UUID of the drive and for awhile it worked but after awhile failed again. So now that I have the time to do this properly, how can I properly set up GRUB2 to use UUIDs so no matter what computer it's in it will work?

---

### Post by TheOnlyMrK on 2011-01-17
Bump.
Found out how to do it using the 40_custom config file but that won't automatically update with kernel updates as far as I can tell.

---

### Post by TheOnlyMrK on 2011-01-17
And just found out this is a bug over a year old. ( [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435) )God I wish their was a portable version of Windows so I could stop dealing with this bs. x.x Am just going to switch to the original GRUB and see if that works.

---

