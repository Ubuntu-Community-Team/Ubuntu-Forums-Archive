---
title: "VMWare Gparted, Ubuntu &amp; GRUB2 who is the right one"
date: 2011-03-23
forum: General Help
---

### Post by savithari on 2011-03-23
I have a working Ubuntu 64 bit inside Guest in a Windoze7 host env.

It was originally at 40gb all working fine.

I have since then *resized *it to 18gb using _Gparted _(dont need 40gb).

I have also created another disk of 20 gb. Let us call this Disk2.

I then used gparted and** copied the parition from the 18gb to Disk2**.

I marked Disk2  as bootable with the flags options of gparted. I removed the original drive.

When I connected the new drive aka Disk2  by itself and restarted the machine,_** I am seeing blank screen.**_

I am not sure if MBR is copied or how to get GRUB2 into this scenario.

Any ideas would help.

---

### Post by savithari on 2011-03-23
I am trying to see if there is something I need to set in the grub2 for this to work right.

---

