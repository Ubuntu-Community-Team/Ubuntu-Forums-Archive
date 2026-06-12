---
title: "Jaunty 32 to jaunty 64."
date: 2009-10-03
forum: General Help
---

### Post by Guy Sibley on 2009-10-03
I mistakenly installed 32-bit os on my machine and I was wondering if there was any way to upgrade to 64bit without losing all of my settings and data? 
Thanks friends.

---

### Post by beastrace91 on 2009-10-03
Not quiet. You could go in and manually back up the data from each application, but no there is not a clean way to 'upgrade' from 32bit to 64bit.

~Jeff

---

### Post by drs305 on 2009-10-03
> **Guy Sibley said:**
> I mistakenly installed 32-bit os on my machine and I was wondering if there was any way to upgrade to 64bit without losing all of my settings and data? 
Thanks friends.

You have to do a clean install to upgrade to 64-bit. If you have a separate home most of your configuration settings can be preserved. You need to reinstall, do manual partitioning, designate the separate /home partition, and *make sure not to format that partition*.

To create a separate /home partition, here is a guide:
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Added: Synaptic has a feature that allows you to save a list of your currently-installed apps. You can then import it to a new installation. Synaptic > File > Save Settings (make sure you tick "Save full state". Save it to a location that won't be formatted on the clean install. On the new machine, Synaptic > File > Read Markings.

---

### Post by Guy Sibley on 2009-10-03
Ok thanks, I was kinda afraid of that. Thank you for all the advice. I really dont like being without a whole gig of my ram.

---

### Post by 3rdalbum on 2009-10-03
If you don't have a seperate /home partition, then just back up the entire contents of your home directory (INCLUDING the hidden folders inside), install 64-bit Ubuntu, and copy them back if necessary.

The Ubuntu installer now has a feature whereby it will still preserve the contents of your old system's home directories, as long as you don't tick the "Format?" checkbox for your old / partition in the "manual partitioning" screen. This has worked for me twice in the past, but whenever you're making widescale changes to your disk you should be operating with a backup anyway.

---

### Post by drs305 on 2009-10-03
> **3rdalbum said:**
> The Ubuntu installer now has a feature whereby it will still preserve the contents of your old system's home directories, as long as you don't tick the "Format?" checkbox for your old / partition in the "manual partitioning" screen.


3rdalbum,

Do you know what happens to unneeded files from the old install if you don't format the old / partition? Does the installation remove everything from the old install *except* necessary configuration files?

---

