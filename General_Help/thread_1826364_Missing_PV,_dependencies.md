---
title: "Missing PV, dependencies"
date: 2011-08-16
forum: General Help
---

### Post by zeromx on 2011-08-16
Hello everyone,

Im following [http://elinux.org/BeagleBoardUbuntu#Demo_Image](http://elinux.org/BeagleBoardUbuntu#Demo_Image) to install ubuntu on my beagleboard via Ubuntu 10.10 on liveCD.

When i enter this command in terminal.
"sudo ./setup_sdcard.sh --mmc /dev/sdX --uboot beagle"

It gives me a error sayings Dependencies are missing.

"Missing pv

Your System is Missing some dependencies
Ubuntu/Debian: sudo apt-get install uboot-mkimage wget pv dosfstools btrfs-tools parted"

and when i enter the that above in terminal i get the following error.
unable to locate PV

---

### Post by skinnyquiver on 2011-08-16
Try
apt-get update
apt-cache search ^pv #please post results
cat /etc/issue #please post results

> **zeromx said:**
> Hello everyone,

Im following [http://elinux.org/BeagleBoardUbuntu#Demo_Image](http://elinux.org/BeagleBoardUbuntu#Demo_Image) to install ubuntu on my beagleboard via Ubuntu 10.10 on liveCD.

When i enter this command in terminal.
"sudo ./setup_sdcard.sh --mmc /dev/sdX --uboot beagle"

It gives me a error sayings Dependencies are missing.

"Missing pv

Your System is Missing some dependencies
Ubuntu/Debian: sudo apt-get install uboot-mkimage wget pv dosfstools btrfs-tools parted"

and when i enter the that above in terminal i get the following error.
unable to locate PV

---

### Post by zeromx on 2011-08-16
Your a star, i tried apt-get update but didnt do much.

Can you explain what did apt-cache search ^pv do?...

---

### Post by skinnyquiver on 2011-08-16
> **zeromx said:**
> Your a star, i tried apt-get update but didnt do much.

Can you explain what did apt-cache search ^pv do?...

it should have listed results of all the packages your system can find that begin with pv 
here are the results from my system
mysystemname:~$ apt-cache search ^pv
pv - Shell pipeline element to meter data passing through
pvm - Parallel Virtual Machine - binaries
pvm-dev - Parallel Virtual Machine - development files
pvm-examples - Parallel Virtual Machine - examples
pvpgn - Gaming server that emulates Battle.net(R)
pvrg-jpeg - Stanford PVRG JPEG tool
slang-pvm - PVM (Parallel Virtual Machine) interface for S-Lang

from this i can see that apt knows about pv and that apt-get install pv would work

so if you can submit the results of the command to me I will be able to see what your system is showing

---

### Post by zeromx on 2011-08-17
> **skinnyquiver said:**
> it should have listed results of all the packages your system can find that begin with pv 
here are the results from my system
mysystemname:~$ apt-cache search ^pv
pv - Shell pipeline element to meter data passing through
pvm - Parallel Virtual Machine - binaries
pvm-dev - Parallel Virtual Machine - development files
pvm-examples - Parallel Virtual Machine - examples
pvpgn - Gaming server that emulates Battle.net(R)
pvrg-jpeg - Stanford PVRG JPEG tool
slang-pvm - PVM (Parallel Virtual Machine) interface for S-Lang

from this i can see that apt knows about pv and that apt-get install pv would work

so if you can submit the results of the command to me I will be able to see what your system is showing

Thank you, its working now.. i tried that command several times and with no luck but then suddenly it started to work..

Thank you everyone for your help/support.

---

### Post by skinnyquiver on 2011-08-22
> **zeromx said:**
> Thank you, its working now.. i tried that command several times and with no luck but then suddenly it started to work..

Thank you everyone for your help/support.

It was probably the apt-get update that fixed the problem.

---

