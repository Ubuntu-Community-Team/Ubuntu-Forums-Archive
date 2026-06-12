---
title: "ERROR Mounting Portable USB Drive"
date: 2011-07-13
forum: General Help
---

### Post by jjb2011 on 2011-07-13
I have spent the summer and just got my few must-have Windows programs over to Ubuntu 11.04 (64-bit), got it customized with Docky (under Ubuntu Classic) and everything is SWEET. (But don't get me going on Unity dock). 

One problem: if I boot with my 1TB portable hard drive plugged in Ubuntu will recognize it. If I plug a portable drive in after the boot, I get this error below. I tried Mounting manually and with Archive Mount but no deal. Any ideas? Students give me usb keys all the time so this is a major issue for me (or will be in the fall!).

---

### Post by ~!geek!~ on 2011-07-13
I use a gui to manage my system's storage devices. 
You may give it a try if you want.
To install put the following code in terminal.
> sudo apt-get install pysdm
Then start the storage manager you installed after putting the external storage device using command 
> sudo pysdm
Then you may configure the device from there.

Second attempt:
I don't know if I am right or not, but I would suggest you to rename the directory in /media called sdb1 to something say sdb1backup without connecting any external storage device. Now try to connect some external storage device. (No idea what I m saying here i.e. why askin you to back the mount point up so that you may again get original directory back).

---

