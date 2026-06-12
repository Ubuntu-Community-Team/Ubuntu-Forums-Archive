---
title: "Updating 10.04 to 10.10 via CD"
date: 2010-10-14
forum: General Help
---

### Post by FeyerbrandX on 2010-10-14
Due to networking issues within 10.04, I can't connect to the internet to update to 10.10.

I've created an install CD, but want to confirm if I'm doing it right, or how to fix some issues I'm seeing.

First, I get the option to create besides my other OS (Vista and currently 10.04).  I've tried to select this option, and it gives 3 options to install:

An SD card I've left in my computer
Sharing my Vista HD
Sharing with 10.04.

The issue is that when I got the computer, I partitioned my second HD (320GB) in half, one that is shared with Vista as a storage dump, the second half Ubuntu (160GB partition).

Currently, using this option forces me to split this half partition between Lucid and Maverick.  For some reason, if I try and "use entire partition" the bar shows 2GB as the size of the partition.  If I choose use entire HD, it shows the full 320GB.  Using the slider can reduce the footprint of Lucid, but can't wipe it out.

Since I haven't screwed around with partitions too much in the last 3 years, I am not too comfortable with using the advanced option, but it seems like the only chance I have to erase 10.04 completely.  This is reinforced by it asking about "device for boot loader"

Any help would be appreciated.

---

### Post by TBABill on 2010-10-14
If I'm not mistaken, isn't there an option to choose "use existing partitions"? Then you choose the one where 10.04 currently resides and just install 10.10 to that partition. From what you described you are trying to move up to 10.10, not keep 10.10 and 10.04 on separate partitions.

---

### Post by FeyerbrandX on 2010-10-14
As I said, for some reason it will create a 2GB partition, rather than the 160 GB partition you would expect.  And I'm not about to push the forward button if it looks like it'll ignore 98% of the partition. 

These screen caps show the result of that button.  You can see it is still pointing towards the same (0,0,0) position on the drive, and it didn't decide to go back to the SD card or anything.

---

### Post by TBABill on 2010-10-14
I think you should be selecting "use entire partition" so it will use the whole thing, not divide it between 10.04 and 10.10. Do NOT select the other, obviously, or it will use the whole hard drive.

---

### Post by aysiu on 2010-10-14
If you're upgrading and not reinstalling, you should use the Ubuntu 10.10 Alternate CD and add it as a repository instead of booting it.

---

### Post by FeyerbrandX on 2010-10-14
> **aysiu said:**
> If you're upgrading and not reinstalling, you should use the Ubuntu 10.10 Alternate CD and add it as a repository instead of booting it.

Unfortunately I tried that first, both with the 10.04 and 10.10 alternate isos (burned discs AND mounted)


It gets to the second step and spits this out:  > Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. 

 This can be caused by: 
 * Upgrading to a pre-release version of Ubuntu 
 * Running the current pre-release version of Ubuntu 
 * Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Which really drives me crazy.  I do actually have some restricted format packages on my computer, which may be the last cause listed. But synaptic, or update manager, or anything else can't seem to bring themselves to UNINSTALL anything without having a network connection, for some reason, so I can't try and eliminate them and retry.  I think I need to raze that system to the ground and salt the earth behind me.

As far as going between "entire partition" and "entire drive,"  I really don't have an attachment to the remaining 150 GB that is currently acting as a dump.  The only fear is that I don't want to screw up the bootloader.

I remember having to wipe Vista and install Ubuntu first with 8.04.  IF I choose to use the entire drive, would it screw things up?

---

### Post by TBABill on 2010-10-15
Just a couple things. When you install normally it will reload Grub2. Shouldn't be an issue but you could have to go back and configure Grub2 again if it doesn't see your Vista partition. Plenty of posts on here how to do it. I haven't had to in ages and all my Ubuntu installs lately have found my Windows 7 partition. Just don't have the LiveCD touch that partition and you should be fine.
 
The other thing...I would not recommend loading Ubuntu and then Windows. The Grub2 boot loader is setup to find all operating systems and allow you to boot from them. If you install Windows after an Ubuntu install you will reinstall the Windows boot loader, which doesn't care about your Ubuntu partition. I'm not sure it would change the Ubuntu partition by default, but I have also not tried to load Windows second. Most recommendations on here are for you to load Windows (or leave it loaded) and then install Ubuntu so you boot from Grub2 on each restart.

---

### Post by Quackers on 2010-10-15
Are you trying to install 10.10 on your "second HD (320GB)"? If you are, and are selecting "side by side" installation there is no disc space for it to go on. The disc is fully used (160GB is for Vista and 160GB is for 10.04).
Or have I read it wrong?

---

