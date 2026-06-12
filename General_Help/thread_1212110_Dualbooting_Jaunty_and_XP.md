---
title: "Dualbooting Jaunty and XP"
date: 2009-07-13
forum: General Help
---

### Post by apocryphalbeing on 2009-07-13
So, I installed Jaunty on my laptop, using the default 'use entire disk' install.

Now I've been trying to follow this guide to dual booting Win XP with Linux:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I've resized the Linux partition without any problems, but the Xp install cd wont recognize The empty space left to install. I have formatted the new space in fat32, since windows should at least be able to detect that, but I've had no luck. Is there any way i can get the Xp cd to recognise the partition, without having to format everything and start from scratch?

Might this have anything to do with the kind of partition table linux uses as opposed to that used by windows?

---

### Post by nacho32 on 2009-07-13
really you should have installed XP first alot less of a head ache.

---

### Post by ajgreeny on 2009-07-13
In the freespace you made by shrinking the ubuntu partition, use the ubuntu live CD partition editor to make an ntfs formatted partition, and then I think XP will see it when you go to install.

Windows is not clever enough to see empty space that was once ext3.

When you have windows running properly, restore grub using the way shown in your link, a very slow site in my experience, or following this link.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
It's the work of a few seconds or minutes so don't worry about nacho32's comment, he's right, it is easier the other way, but not difficult your way, so certainly not worth doing if you have ubuntu running well already.

---

