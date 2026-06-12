---
title: "First user logged in can read/write to NTFS partition, but others cannot."
date: 2011-11-02
forum: General Help
---

### Post by silentwords on 2011-11-02
I am configuring a dualboot system for two users, my mom and her roommate.

It's a clean install of Ocelot, brand new hardware, everything else is smooth as silk. I've got it all dialed in in terms of sharing the Firefox and Thunderbird profiles between the operating systems.

The problem is that only whoever logs into Ubuntu first can access the NTFS partition. It doesn't matter which user, both are administrators, but whoever logs in first get's access, the other gets a permission error. Repeatable, and switchable on reboot.

For clarity, both users can see the mounted drive in /media
Only the first user logged into the system from reboot can access it.

I did some searching for this issue last night, but did not find anything in particular. I'm sure there's some line I can add to some file that will make it all work, but I'm a Linux noob.

---

### Post by dcstar on 2011-11-03
> **silentwords said:**
> I am configuring a dualboot system for two users, my mom and her roommate.

It's a clean install of Ocelot, brand new hardware, everything else is smooth as silk. I've got it all dialed in in terms of sharing the Firefox and Thunderbird profiles between the operating systems.

The problem is that only whoever logs into Ubuntu first can access the NTFS partition. It doesn't matter which user, both are administrators, but whoever logs in first get's access, the other gets a permission error. Repeatable, and switchable on reboot.

For clarity, both users can see the mounted drive in /media
Only the first user logged into the system from reboot can access it.

I did some searching for this issue last night, but did not find anything in particular. I'm sure there's some line I can add to some file that will make it all work, but I'm a Linux noob.

Use the **pysdm** package to put the drive into /etc/fstab on a /mnt mount point. The current behaviour is exactly as it should be.

---

### Post by silentwords on 2011-11-03
A tip of the hat and a thanks to you sir!

To help anyone else with the same setup, this is what fixed it for me:

Install **Storage Device Manager** from the **Software Center**.

Use **Disk Utility** to identify the name of the partition. In my case it was *sda2*.

Use **Storage Device Manager**. Select the partition you wish to modify. Click the*** Assistant*** button, and on the* Mount* tab, check the box next to*** "Allow any user to mount the file system"***.

I also had to tweak a couple of the other settings on the *Mount* tab in order to gain permissions to the files on the drive. I added both users to the admin group and gave that group ID read/write permissions. Not sure if that's recommended, but it worked for me.

Reboot

---

