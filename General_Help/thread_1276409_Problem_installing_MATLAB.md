---
title: "Problem installing MATLAB"
date: 2009-09-27
forum: General Help
---

### Post by eerike on 2009-09-27
Hi there
I´m new with Ubuntu and I am trying to install MATLAB, but I´m having some troubles which I hope someone can help me with. I´ve downloaded a MATLAB .iso-file which my school provided and I have done the following steps:
1. Standing in /home/erik/downloads/ 
2. sudu -i (and recieved root access)
3. mkdir /usr/local/matlab
4. mount matlab2008b_Linux_Mac_Sun.iso matlab/
5. ./install
This launches a GUI installation, I go through the steps and choose /usr/local/matlab as directory and connect to the internet to get my student key verified. I press Begin Install and then I get the message:  "There was an error extracting the archives for MATLAB. Check that you have enough disk space and rerun the installer".
6. Close the GUI
7. df -Th
This step show that file system mounted at / is used to 2% and have 425GB free space.

Anyone got an idea of what might be wrong, because I´m lost.

---

### Post by XCan on 2009-09-27
Could you post the output of df? Perhaps matlab uses temp dirs like /tmp/ or another mount path when it extracts?

---

### Post by eerike on 2009-09-27
I forgot that I actually wrote "-o loop" as well in step 4,

Anyways, the results of df -Th is:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    453G  6.0G  424G   2% /
tmpfs        tmpfs   1007M     0 1007M   0% /lib/init/rw
varrun       tmpfs   1007M  212K 1006M   1% /var/run
varlock      tmpfs   1007M     0 1007M   0% /var/lock
udev         tmpfs   1007M  152K 1007M   1% /dev
tmpfs        tmpfs   1007M  484K 1006M   1% /dev/shm
lrm          tmpfs   1007M  2.2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sdb1     vfat    466G  430G   37G  93% /media/EXTERN
/dev/loop0 iso9660    3.9G  3.9G     0 100% /home/erik/Dowloads/matlab

Is that any help?

---

