---
title: "Grub2 has problems with newly cloned Karmic part. (Gparted)"
date: 2010-12-25
forum: General Help
---

### Post by Gossamer T. Jones on 2010-12-25
Hello. I have two drives each with Windoze and one has Karmic. I had no problems using Gparted to copy and paste the Ubuntu 9.10 partition into unallocated space on the second drive.

Now I realize I need to update grub2 to recognize the changes. I've followed [these]("http://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") instructions.

I can boot from the livecd, run fdisk -l, and mount the partition (actually I need to run the --recheck flag or it won't work.)

Then it says to reboot and run sudo update-grub.

When I reboot, it goes to the grub rescue prompt saying "file not found".

I've tried this several times to no avail and I suspect I must be mounting the wrong partition, but it is the only Linux partition that shows. I even tried the NTFS boot partition and the extended partition.

And ideas?

Thanks

-I've searched for this problem and found dozens of different variations including legacy grub suggestions, but I haven't found a solution. Sorry if it's a duplicate.

---

### Post by Gossamer T. Jones on 2010-12-25
Rescatux live cd with a grub restore option (through rescueapp) fixed it!

I've fought with this for three days and finally when I post, it's fixed right away. Figures.

---

