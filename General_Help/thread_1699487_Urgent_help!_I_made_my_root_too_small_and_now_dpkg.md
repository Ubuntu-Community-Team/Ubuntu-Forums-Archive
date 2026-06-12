---
title: "Urgent help! I made my root too small and now dpkg won't work."
date: 2011-03-03
forum: General Help
---

### Post by ac90b671 on 2011-03-03
So I was doing a dist-upgrade and install of "openbravo-erp" on synaptic on my desktop computer. The installation failed complaining about disk space. So I promptly deleted 30gb of junk out of my .wine and download directories, but the os continued to complain, so I rebooted. 

When I got to the login screen (the default gnome login screen not the normal ubuntu theme for some reason), logging in fails and returns me to the same login with the error message "Install problem! The gnome configuration defaults for gnome power manager have not been installed correctly"

From ssh I can get the following info I can think could help get some answers.


```
sudo dpkg --configure -a
```
```

dpkg: failed to write status database record about 'libxml2' to '/var/lib/dpkg/status': No space left on device


```



```
df -h
``` 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/nvidia_ccdhfaeg1
                      9.2G  9.2G     0 100% /
none                  1.5G  288K  1.5G   1% /dev
none                  1.5G     0  1.5G   0% /dev/shm
none                  1.5G  224K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  9.2G  9.2G     0 100% /var/lib/ureadahead/debugfs
/dev/mapper/nvidia_ccdhfaeg3
                      134G   45G   83G  36% /home

```

I can now clearly see I filled my root of my drive up. I was apparently wrong thinking 10gb was enough for my system. Without a working dpkg I have no idea how to get things working again, that is how to free up system space without dpkg. Let me know if there's any other output you need to see. Thanks in advance.

---

### Post by oldfred on 2011-03-03
Are you running RAID or LVM? the /dev/mapper says something and I do not know the details on how you mount that or if it is just the same.

You can chroot into your system and houseclean & update. I have installed a lot of software and only used about 6GB. It looks like the housecleaning you did was in /home not / (root).

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)


#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
#

You may not have emptied all the trash or have run a backup that defaulted into /?

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by Austin25 on 2011-03-03
You could use a live CD or flash drive to change your partition sizes.

---

### Post by ac90b671 on 2011-03-03
First off, my hard drive is a raid array on which I have partition 1 as "/" partition 2 as swap space and partition 3 as "/home".

From
```
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
```
```

78256	linux-headers-2.6.35-22
78280	linux-headers-2.6.35-27
78284	linux-headers-2.6.35-25
78320	linux-headers-2.6.35-28
78324	linux-headers-2.6.35-26
81020	google-chrome-unstable
94920	ttf-umefont
97940	wine1.3
108216	fglrx
133864	ubuntu-docs
134616	libreoffice-core
135488	linux-image-2.6.35-22-generic
135596	linux-image-2.6.35-26-generic
135604	linux-image-2.6.35-25-generic
135608	linux-image-2.6.35-27-generic
135608	linux-image-2.6.35-28-generic
206032	ia32-libs
255264	texlive-latex-extra-doc
263876	openjdk-6-doc
1117456	openbravo-erp
```
I can see that openbravo takes up at least 1.3GB and is probably what filled up the disk.

Currently any apt command complains about dpkg not working. For example:
```
apt-get autoclean
```
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```
And 'sudo dpkg --configure -a' doesn't work either.

I'll try > You could use a live CD or flash drive to change your partition sizes.
and expand my root into the swap space and see if that makes dpkg run correctly. I'll post back with my results.

---

### Post by ac90b671 on 2011-03-03
I didn't have luck for some reason. Gparted in the live cd I had crashed shortly after startup every time. No explanation there. I then booted up the computer again and 'ssh'ed into it with X forwarding on and got gparted up that way. Problem there was that gparted only saw the physical disks of the array as unallocated space but didn't see the raid drive. Running 
```
sudo fdisk /dev/mapper/
```got
```

last_lba(): I don't know how to handle files with mode 40755
You will not be able to write the partition table.

Unable to read /dev/mapper/

```

Any other ideas to partition my disk or otherwise?

---

### Post by oldfred on 2011-03-04
Whenever gparted or many other programs do not work, sometimes a filecheck is all that is required.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

