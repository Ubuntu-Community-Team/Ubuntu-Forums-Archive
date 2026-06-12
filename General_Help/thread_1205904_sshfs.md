---
title: "sshfs"
date: 2009-07-06
forum: General Help
---

### Post by jhapk on 2009-07-06
Hi,

I am trying to install "sshfs" by
 
sudo apt-get install sshfs

but get an error with the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxine1-x libxine1-misc-plugins libxcb-xv0 libmagick10 libxine1-bin libxcb-shape0 libmodplug0c2 libxcb-shm0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  sshfs
0 upgraded, 1 newly installed, 0 to remove and 28 not upgraded.
Need to get 39.6kB of archives.
After this operation, 143kB of additional disk space will be used.
Get:1 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) intrepid/main sshfs 2.0-2 [39.6kB]
Fetched 1143B in 18s (61B/s)                        
Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/pool/main/s/sshfs-fuse/sshfs_2.0-2_i386.deb](http://tw.archive.ubuntu.com/ubuntu/pool/main/s/sshfs-fuse/sshfs_2.0-2_i386.deb) Size mismatch
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

any insights?

Thanks

---

### Post by iver2435 on 2009-07-06
Have you tried running the commands listed in the error message?

---

### Post by jhapk on 2009-07-06
sorry! I didn't do that before.
Now I did it and it runs fine.

Thanks.

---

### Post by t0p on 2009-07-06
> **jhapk said:**
> sorry! I didn't do that before.
Now I did it and it runs fine.


Jolly good!

When an error message suggests a command to fix the problem, it's a good idea to try it out.  Usually (but not always) it will fix the problem.  Definitely worth a go.

---

