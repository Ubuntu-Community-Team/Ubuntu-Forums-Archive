---
title: "hey guys, nub here needs help"
date: 2010-07-05
forum: General Help
---

### Post by michaelJoker on 2010-07-05
100gb total hard disk space  I am left with 40gb hard disk space now, I check by right clicking on the file system then clicking on properties...  but the problem is...when I key sudo du -hs under /, it states 18G rather than 60G...  are there ways that I can found out what is choking up all my hard disk space?

---

### Post by oldfred on 2010-07-05
Back to OP's original question.

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

Mounted Partition use:
df -Th | sort

---

### Post by Johnny B on 2010-07-05
i would use 'df -h' and the disk usage analyzer to find whats eating up your space.

More housekeeping if you're interested, this is from a script:
```
OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)

echo "Cleaning apt cache..."
sudo aptitude clean 

echo "Removing old config files..."
sudo aptitude purge $OLDCONF

echo "Removing old kernels..."
sudo aptitude purge $OLDKERNELS 
```

---

