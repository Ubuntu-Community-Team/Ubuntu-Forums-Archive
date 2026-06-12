---
title: "Change Label on a windows drive"
date: 2010-11-05
forum: General Help
---

### Post by marshall1001 on 2010-11-05
This isn't important but it's always been an itch I can't figure out.

I have 3 partitions on my laptop: Ubuntu, OSx86 and Windows 7. I use Pysdm Storage Device Manager to automount them on start-up.

My OSx86 partition is labelled "OS X" and displays as such on all three systems. My Windows partition displays as "80GB File System" (as it's meant to).

I was just wondering whether or not it was possible to change how it displays on Ubuntu safely, to something more aesthetically pleasing such as "Win7".

---

### Post by searchfgold6789 on 2010-11-05
[LIST=1]
[*]In Linux, download GParted.
[*]Open GParted.
[*]In the dropdown menu in the upper right hand corner of the program, select your device.
[*]Right click the device and click Unmount.
[*]Right click the device again and click Label.
[*]Type in the new label and click OK.
[*]Click the green check mark to apply the operation.
[/LIST]
Then you're all set.

---

### Post by drs305 on 2010-11-05
In the newer versions of Ubuntu it can also be done via System, Administration, Disk Utility. Highlight the partition, then "Edit Filesystem Label".

Please mark this thread SOLVED via the 'Thread Tools' link near the top right of the original post once you have seen enough ways to do what you want.

---

### Post by marshall1001 on 2010-11-05
Cheers, I didn't want to use Gparted originally because I thought it may affect Windows itself.

---

### Post by coffeecat on 2010-11-05
> **marshall1001 said:**
> Cheers, I didn't want to use Gparted originally because I thought it may affect Windows itself.

As a point of information you could have added/changed the partition label in Windows. Simply open a 'Computer' explorer window, right-click on the C: drive and choose 'Rename'.

But it's much more satisfying doing this in Ubuntu. :)

---

