---
title: "Increase Swap space!!!!!"
date: 2009-12-22
forum: General Help
---

### Post by aminmatrix on 2009-12-22
hi 
i have  ubuntu 9.10
i have only 256Mb in Swap partion
how can i increase it!?

---

### Post by byStanderone on 2009-12-22
...you can use gparted to do that, but it depends if you have the availabe space to grow your swap, and shrink the neighboring partition, but i think ubuntu would be fine with your present swap capacity, unless you find it otherwise.

---

### Post by aminmatrix on 2009-12-22
Actually, *yes*. You can supplement your swap partition with a swap *file*. It goes something like this:

First, create a large empty file:
 	Code:
 	sudo dd if=/dev/zero of=/swap_file bs=1M count=1000 
Replace 1000 with the size of the swap file desired, in MB. You can also put the swap_file in a different location if desired.

Next, we'll secure the swapspace, so ordinary users cannot read the contents (potential security breach):
 	Code:
 	sudo chown root:root /swap_file
sudo chmod 600 /swap_file 
Then, turn it into swap space:

 	Code:
 	sudo mkswap /swap_file 
Next, turn it on:
 	Code:
 	sudo swapon /swap_file 

To make it turn on at every bootup, open up /etc/fstab:
 	Code:
 	sudo gedit /etc/fstab 
Add this line to the end of the file:
 	Code:
 	/swap_file       none            swap    sw              0       0

---

### Post by byStanderone on 2009-12-22
...oh, i see, thanks for that one, merry christmas!

---

