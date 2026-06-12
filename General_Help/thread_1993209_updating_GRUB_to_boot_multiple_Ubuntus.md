---
title: "updating GRUB to boot multiple Ubuntus"
date: 2012-06-01
forum: General Help
---

### Post by Ceiber Boy on 2012-06-01
I've added a second HDD to my computer with an instance of Ubuntu installed (from a different machine), when i boot my computer i want grub to give me the option of booting into either instance of Ubuntu on either disk

how do i do this?

Thus far i have tried:
sudo update-grub
sudo grub-install /dev/sdb

---

### Post by oldfred on 2012-06-01
The sudo update-grub should have found the install if the external drive was plugged in. Sometimes it may need to be mounted first? It would be better to boot the external and install its grub to the MBR of the external.

Run the boot-info report from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by flemur13013 on 2012-06-01
If you have two physical disks you might be able to select the boot disk from BIOS: you'll have two independent systems that can see each other's disks/partitions, and if each booted separately before they should still do so (minus any problems due to different hardware Edit: and assuming the 'update-grub', etc, didn't break it).  Doing this has no down-side that I'm aware of, and you avoid messing with that grub POS.

---

### Post by argief on 2012-08-31
Go poke around in /boot/grub (you may need to mount boot just remember).  There is a file called grub.cfg.  The answer is that you will need a duplicate copy of the ubuntu entries, with just ONE change: --set=root a40ec3c3-f72c-4c0a-a41e-9b0ffe2f should be the UUID of the partition on your external drive.

When you are done breaking the ubuntu way of trying to make everything easier... ;-)  You can change these settings in the grub config file in /etc/grub.d/40_custom.

I can give your more detail if you'd like but the steps are above, dont want to sound patronizing!

---

