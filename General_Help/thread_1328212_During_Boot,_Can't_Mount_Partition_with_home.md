---
title: "During Boot, Can't Mount Partition with /home"
date: 2009-11-16
forum: General Help
---

### Post by stephen67 on 2009-11-16
I am using 9.10 applied as an upgrade.

/home is on its own partition, that is on the save disk as /.

I think I filled, or came close the filling /home while I was copying files across my network and I was working on something else.

I use a KVM switch.

When I switched back to Ubuntu, the mouse and keyboard did not have any effect. I found plugging the USD keyboard and USB mouse directly into the computer did not work.

I had to pull out an old PS/2 keyboard and mouse.

During boot, I get an error saying the partition with /home cannot be mounted.

I am prompted to ESC to a command line and make repairs.

I have downloaded the 9.10 LiveCD.

Tonight I plan to run fsck.

Any other advise/ideas would be greatly appreciated.

Thanks

---

### Post by blueridgedog on 2009-11-16
Can you try and mount the partition manually from the command line and report the error?

sudo mkdir /mnt/homedisk
sudo mount /dev/sda3 /mnt/homedisk

(change sda3 to your disk/partition, as it is just an example).

---

