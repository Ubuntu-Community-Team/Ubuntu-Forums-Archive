---
title: "Trouble with Software Update Manager/resizing partions."
date: 2009-11-14
forum: General Help
---

### Post by El_Choclo on 2009-11-14
Hello everyone.  First post from a noobie.

I have turned an old Dell workstation into an Ubuntu 9.04 home media server, backup solution, and file repository using LAMP, Samba, and Jinzora.  I upgraded this old box with 2 WD Caviar 1TB SATA drives and partitioned them as follows:
/boot= 500 MB
/var=  5 GB
/swap= 20 GB
/data= the rest @950GB

All has been well until today.  I am attempting to install updates with Software Update Manager.  I receive this error message:
"The upgrade needs a total of 29.4M free space on disk '/var'. Please free at least an additional 29.4M of disk space on '/var'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

Ok, fine.  So I look at GParted and sure enough, I have filled up the /var partition 100%
When I run df -h from the terminal, I see this:
Filesystem            Size  Used Avail Use% Mounted on
/dev/md3              894G   97G  752G  12% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  2.0M  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  184K  1.7G   1% /dev
tmpfs                 1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G  2.5M  1.7G   1% /lib/modules/2.6.28-16-server/volatile
/dev/md0              471M   53M  395M  12% /boot
/dev/md1              4.6G  4.5G     0 100% /var

I boot the machine with a GParted disk and resize the /var partition from 5 GB to 25GB.
I then restart the machine and open GParted to verify the changes.  Looks great:  /var is now 25 GB and 80% unused.  Perfect.

However, I still receive the error message from Software Update Manager that /var is full.  Also, when I run df -h from the terminal, it still shows the /var partition is 4.6 GB and 100% full.  I performed a successful check and repair of this partition using GParted, but it did not resolve the issue.  

In short:
GParted says /var is 24.80 GB and 80% unused.
df -h says /var is 4.6 GB and 100% used.

What am I missing?  Thanks!

---

