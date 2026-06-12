---
title: "dpkg E: Sub-process returned an error code"
date: 2011-01-28
forum: General Help
---

### Post by rubylaser on 2011-01-28
I was trying to do an update on my NFS server and had some packages fail to install properly.  I've tried all the usual stuff.  This is a 64 bit 10.04 Server install, with lots of available hard drive space.

```
root@svr-cc-marketing:/var/marketing# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1      46G  1.5G   43G   4% /
none                  4.0G  204K  4.0G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G   88K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
none                   46G  1.5G   43G   4% /var/lib/ureadahead/debugfs
/dev/cciss/c0d0p3     901G  473G  428G  53% /var/marketing
root@svr-cc-marketing:/var/marketing# 

```

Here's the output of some common commands.
```
root@svr-cc-marketing:/var/marketing# apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
E: Sub-process returned an error code
```
```
apt-get upgrade
```
```
root@svr-cc-marketing:/var/marketing# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  samba
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  bsdutils libblkid1 libuuid1 mount nfs-common nfs-kernel-server portmap util-linux
  uuid-runtime
9 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 1,516kB of archives.
After this operation, 18.4MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
root@svr-cc-marketing:/var/marketing# dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)

Setting up apparmor (2.5.1-0ubuntu0.10.04.3) ...
mktemp: failed to create file via template `/tmp/tmp.XXXXXXXXXX': No such file or directory
dpkg: error processing apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apparmor-utils:
 apparmor-utils depends on apparmor; however:
  Package apparmor is not configured yet.
dpkg: error processing apparmor-utils (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-27-server
mktemp: failed to create directory via template `/tmp/mkinitramfs_XXXXXX': No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-27-server
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apparmor
 apparmor-utils
 initramfs-tools

```

I've tried to individually reconfigure the packages...
```
root@svr-cc-marketing:/var/marketing# dpkg-reconfigure apparmor
/usr/sbin/dpkg-reconfigure: apparmor is broken or not fully installed

```

I've even tried to purge the packages, but I still can't update, or install new packages.  Here's the output of dpkg --audit...
```
root@svr-cc-marketing:/var/marketing# dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 apparmor-utils       Utilities for controlling AppArmor

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs
 apparmor             User-space parser utility for AppArmor

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 samba                SMB/CIFS file, print, and login server for Unix


```

Any help you can provide to get my package manager functioning again would be greatly appreciated.

---

### Post by rubylaser on 2011-01-31
Bump.  I could really use some ideas.  Thanks.

---

### Post by gmargo on 2011-01-31
"apt-get update" won't even complete?

---

### Post by matt_symes on 2011-01-31
Hi

Have you tried....

```
sudo dpkg --configure -a
sudo apt-get install -f
```

Kind regards

---

### Post by rubylaser on 2011-01-31
Unfortunately, apt-get update fails with an E: Sub-process returned an error code message.  I can do 

```
sudo dpkg --configure -a
sudo apt-get install -f
```

But, neither fixes the previously mentioned problems.  If I try to reinstall any of the packages that don't work, I get this error.
```
E: Could not perform immediate configuration on 'libattr1'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```

---

### Post by pl@yer on 2011-01-31
I take it you tried "dpkg --configure" apparmor and it also failed. If not try that first.

---

### Post by rubylaser on 2011-01-31
Thank you for the input

I'm not sure what has happenned to my server, but the contents of /var/lib/dpkg/status are empty.  At this point I don't think dpkg has a clue what packages are even installed.
```
root@svr-cc-marketing:/var/lib/dpkg# dpkg -l
root@svr-cc-marketing:/var/lib/dpkg# 

```

Is there any way to recreate that file?  At this point it looks like I'll have to reinstall.  My drives are on a HP P400i RAID controller and they all pass a SMART test, so I'm not sure what happened.  If I try to install libattr1, I get this error...
```
Could not perform immediate configuration on 'libselinux1'
```

If I try to install install libselinux1, I just get the same error again.  Any more ideas, or do I need to reinstall?

---

### Post by rubylaser on 2011-01-31
Well, good news.  I happened to have a snapshot of the root folder on my backup drive.  I restored the status file from that backup.  Then I recreated the /tmp folder that was somehow also gone. 
```
mkdir /tmp
```
Finally, I ran these two commands...
```
cd /var/cache/apt/archives
dpkg -i --force-depends initramfs-tools*
```
```
apt-get -f install
```
And now, apt-get update works like a charm :)

Thanks to all that gave advise.

---

### Post by KenBW2 on 2011-07-07
For the record, I fixed this by recreating my /tmp folder (I deleted it when running out of space)

---

