---
title: "Ubuntu only uses 20gb of a 200gb partition"
date: 2011-10-15
forum: General Help
---

### Post by EvanR on 2011-10-15
Hi, I've installed ubuntu on a 200gb partition yet it says the disk space is 20gb, I think this has to do with something I set in the installation. This would be fine but i cannot access the rest of the rest of the partition so there is 180gb of disk space being wasted!

Here is the output of 'df -h':

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             19G   18G  138M 100% /
udev                  1.4G  4.0K  1.4G   1% /dev
tmpfs                 551M  860K  550M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.4G  2.3M  1.4G   1% /run/shm
/dev/sda3             201G   39G  162G  20% /host

Any help would be very much appreciated!

---

### Post by gsmanners on 2011-10-15
I think I'd be more concerned about running off of a loop-mounted file system than where your drive space went. How on Earth did you manage that?

---

### Post by EvanR on 2011-10-15
I ran the installation from a usb stick - did a standard install I didn't do anything out of the ordinary.

What can I do to fix this?

---

### Post by gsmanners on 2011-10-15
Goodness. "Standard" installs aren't really my thing. I always select "Something Else" in that particular dialog (when the installer asks about your drive), and then I select the partitions I want it to use. I use gparted (Gnome partition editor) to set up the partitions before I run the installer, then select the partitions manually when the installer asks about them.

---

### Post by JKyleOKC on 2011-10-15
> **EvanR said:**
> 
```
/dev/sda3             201G   39G  162G  20% /host
```This line in your report leads me to believe that you did a "wubi" install inside of Windows, rather than a normal side-by-side or total-replacement installation. The standalone file system doesn't include a partition named "/host" but wubi does -- it contains all the rest of the 200-GB drive, which may still have a fully functional Windows system on it, although the "df" report shows its space as being free.

If this is the case, you're up the well-known creek since a wubi installation's maximum size is set at installation time and cannot be expanded. With only 138 MB of disk space remaining, you don't have enough room to do much of anything.

Your best bet would be to transfer any files you already have out to a flash drive, use the Windows add/remove utility to remove the Ubuntu installation, and then re-install giving it more space (although 30 GB seems to be the maximum size that the default wubi installation allows). Otherwise you need to do a standalone installation, either side-by-side with Windows, or totally replacing Windows (which may not be a good idea the first time out). No matter which way you go, you can copy your data back from the flash drive into your new system and proceed from there.

---

