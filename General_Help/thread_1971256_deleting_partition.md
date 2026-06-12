---
title: "deleting partition"
date: 2012-05-02
forum: General Help
---

### Post by ulissipus on 2012-05-02
Could anyone tell how to delete a partition (in Precise Pangolin)? I've tried using Disk Utility to no avail: always get a message like "an error occurred while performing an operation on "245GB extended (Partition 2 of ATA ........): The device is busy".
thanks in advance

---

### Post by raja.genupula on 2012-05-02
Hi , yeah the reason is you must **Unmount** the device before doing the operation .

Try again , all the best :)

---

### Post by ulissipus on 2012-05-02
Thanks, but also failed. This time I get a similar message to the effect that "an error occurred while performing an operation on "241GB Filesystem (Partition 5 of ATA...). The operation failed.
O nclicking "Details" I get: Error unmounting: umount exited with exit code 1: helper failed with: umount: only root can unmount UUID=e00666a6-ef12-48c7-90b5-582c0700bf43 from /
best

---

### Post by Zukaro on 2012-05-02
You're probably trying to unmount a partition which is in use (such as /).
(I'm not familiar with the error codes)

But due to the fact it says "only root can umount" then you probably need to be root.  Try using Gparted; I'm not sure about how Disk Utility does it but I know to use Gparted you need to be root (it will ask you to enter your password upon starting it).
(also I find Gparted to be a lot better than the Disk Utility that comes with Ubuntu)

If you wanna try using Gparted just grab it from the software center (search for Gparted and you'll find it).

---

### Post by raja.genupula on 2012-05-02
+1 to Gparted .
other wise do one thing , give a restart and dont mount the partition this time . then do format now .

---

### Post by bodhi.zazen on 2012-05-02
I suggest you manage partitions from a live CD.

---

### Post by jadtech on 2012-05-02
boot from cd/dvd or usb which ever you have, once booted  go to G-parted  to do your partition deleteing  you may have to right click the swap and turn swap off before it will work ..

---

### Post by ulissipus on 2012-05-03
Thanks, folks! I saw it is possible to boot from a live GPart CD. This is probably easier than being root. Will try later, hope it will solve.
Greetings from South Africa!

---

### Post by ulissipus on 2012-05-11
Dear bodhi.zazen & jadtech, 
I was a bit busy lately but finally found time to make the CD and try it. Result as expected - by my: I erased not only the partition but a lot of other things as well (using GParted is not that evident!). So I did what I had thought to do at one staged: reinstalled Ubuntu. Some hard work but no big deal, as I had everything backed up. Thanks for you patience & help, anyway.

---

