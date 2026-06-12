---
title: "ubuntu installation"
date: 2010-11-28
forum: General Help
---

### Post by manishsongara on 2010-11-28
I am beginner user for the Linux ubuntu OS. Presently, I am working on Winows XP Operating system. I want to install the Linux ubuntu OS also on my PC. That is I want to keep both the Operating system in my PC. The hard disc size is 250GB and RAM is 1GB. Please let me know how to install both the OS simultaneously on the same PC. How to make partition on the hard disc (250 GB size) for this purpose.

---

### Post by leclerc65 on 2010-11-28
Use Gparted (google for it) to shrink the C partition. Get out of Gparted, put in the Ubuntu CD and reboot.
... in the partition screen , choose 'Manual'.
Divide the unallocated disk space into:
      ~6G-10G for '/' - ext4
      1G for Swap
      leftover for '/home' - ext4 

After the installation, reboot, you'll see options to choose Ubuntu or Windows.  
Don't forget to open the Terminal (Applications/Accessories/Terminal) and run the 2 following commands:
sudo apt-get update
sudo apt-get upgrade

---

