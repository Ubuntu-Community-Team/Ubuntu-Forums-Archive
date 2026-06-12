---
title: "Need to make Ubuntu stop updating BIOS clock to UTC time."
date: 2011-01-22
forum: General Help
---

### Post by TheOnlyMrK on 2011-01-22
I have Ubuntu 10.04.1 32bit installed on my flash drive so wherever I go I can have my own mini personal computer, but one problem I'm having is every computer it is run on the next time it's rebooted to the OS on the hard drive it has UTC time instead of the actual time for the timezone you're in that Windows uses. So is their a way I can make Ubuntu not automatically change the clock to what it wants?

---

### Post by 101011010010 on 2011-01-22
Hello.
On a normal install I have to edit "/etc/default/rcS" and change the utc line to " UTC=no".
Save and next time you boot it will use local time. If your install is persistent this should work.
I hope this helps.
A.

---

### Post by TheOnlyMrK on 2011-01-22
> **101011010010 said:**
> Hello.
On a normal install I have to edit "/etc/default/rcS" and change the utc line to " UTC=no".
Save and next time you boot it will use local time. If your install is persistent this should work.
I hope this helps.
A.

Thanks it seems to of worked, and yes it's a full install. ~5GB ext2 partition at the end of my flash drive (Since Windows is retarded and refuses to read more than the first partition on a flash drive).

---

