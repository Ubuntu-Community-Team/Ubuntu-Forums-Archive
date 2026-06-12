---
title: "dpkg is broken"
date: 2010-09-21
forum: General Help
---

### Post by eloydark on 2010-09-21
I am experiencing a broken dpkg problem

The problem is somewhat weird:

```

sudo apt-get install -f
[sudo] password for aris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.35-22-generic
The following packages will be upgraded:
  linux-headers-2.6.35-22-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/800kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `linux-headers-generic' missing, assuming package has no files currently installed.
(Reading database ... 309918 files and directories currently installed.)
Preparing to replace linux-headers-2.6.35-22-generic 2.6.35-22.32 (using .../linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb) ...
Unpacking replacement linux-headers-2.6.35-22-generic ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This problem is not fixed with:
dpkg --configure -a 
dpkg-reconfigure
touch /var/lib/dpkg/tmp.ci/md5subs

here is some of the output of 
sudo dpkg --debug=3773 -i /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb 
```

Preparing to replace linux-headers-2.6.35-22-generic 2.6.35-22.32 (using .../linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb) ...
D000001: process_archive oldversionstatus=broken due to failed removal or installation
...
D000002: process_archive info installed /var/lib/dpkg/tmp.ci/postinst as /var/lib/dpkg/info/linux-headers-2.6.35-22-generic.postinst
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb (--install):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
D000010: ensure_pathname_nonexisting running rm -rf
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/reassemble.deb'
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb

```

I could try to post the entire output but it's pretty much around 8MB and I really don't think it's relevant

dpkg is version 1.15.8.4
I am running AMD64 distro with Maverick on ext2 /boot/, ext3 /, xfs /home/

Any input for resolving this would be much appreciated!
Reinstalling ubuntu is not really an option since I have many apps installed that I wish not to reinstall!

---

### Post by lkjoel on 2010-09-21
> **eloydark said:**
> I am experiencing a broken dpkg problem

The problem is somewhat weird:

```

sudo apt-get install -f
[sudo] password for aris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.35-22-generic
The following packages will be upgraded:
  linux-headers-2.6.35-22-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/800kB of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `linux-headers-generic' missing, assuming package has no files currently installed.
(Reading database ... 309918 files and directories currently installed.)
Preparing to replace linux-headers-2.6.35-22-generic 2.6.35-22.32 (using .../linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb) ...
Unpacking replacement linux-headers-2.6.35-22-generic ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This problem is not fixed with:
dpkg --configure -a 
dpkg-reconfigure
touch /var/lib/dpkg/tmp.ci/md5subs

here is some of the output of 
sudo dpkg --debug=3773 -i /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb 
```

Preparing to replace linux-headers-2.6.35-22-generic 2.6.35-22.32 (using .../linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb) ...
D000001: process_archive oldversionstatus=broken due to failed removal or installation
...
D000002: process_archive info installed /var/lib/dpkg/tmp.ci/postinst as /var/lib/dpkg/info/linux-headers-2.6.35-22-generic.postinst
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb (--install):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
D000010: ensure_pathname_nonexisting running rm -rf
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/reassemble.deb'
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.35-22-generic_2.6.35-22.33_amd64.deb

```

I could try to post the entire output but it's pretty much around 8MB and I really don't think it's relevant

dpkg is version 1.15.8.4
I am running AMD64 distro with Maverick on ext2 /boot/, ext3 /, xfs /home/

Any input for resolving this would be much appreciated!
Reinstalling ubuntu is not really an option since I have many apps installed that I wish not to reinstall!
Try:
```
sudo apt-build build-source linux-headers-2.6.35-22-generic
sudo apt-build install linux-headers-2.6.35-22-generic

```

---

### Post by eloydark on 2010-09-21
> **lkjoel said:**
> Try:
```
sudo apt-build build-source linux-headers-2.6.35-22-generic
sudo apt-build install linux-headers-2.6.35-22-generic

```

Needless to say, package apt-build was not installed but I installed it via dpkg (some errors on the way of course but appeared to be installed with the dependencies)
Next I created the /etc/apt/apt-build.conf file with 
```
build-dir = /home/aris/var/cache/apt-build/build
```
(It would not run without it)
Then
```
sudo apt-build build-source linux-headers-2.6.35-22-generic
Building the following packages from source: 
-----> Installing build dependencies (for linux) <-----
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-meta' as source package instead of 'linux'
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
22 not fully installed or removed.
E: I wasn't able to locate file for the linux-headers-2.6.35-22-generic package. This might mean you need to manually fix this package.
E: Failed to process build dependencies
........
-----> Downloading source linux (2.6.35-22.33) <-----
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-meta' as source package instead of 'linux'
E: Ignore unavailable version '2.6.35-22.33' of package 'linux'
E: Unable to find a source package for linux-meta
-----> Building linux <-----
Can't chdir(linux-2.6.35): No such file or directory at (eval 4) line 4
	main::__ANON__('linux-2.6.35') called at /usr/bin/apt-build line 288
	main::build('linux', 2.6.35, -22.33) called at /usr/bin/apt-build line 630
	main::build_source called at /usr/bin/apt-build line 82

```

---

### Post by eloydark on 2010-09-22
So now I am downloading the sources and the dependencies to build the kernel from scratch. I am pretty much desperate at this stage since I am pretty sure that I will eventually have to make a clean install.

Apt-build is still not working, I believe there is something wrong with the sources.list file. 

In the sources.list.d directory the apt-build repos where wrongly named (for no apparent reason), I have manually renamed them with the appropriate extention but it's still a no-go.

Also I have run a fsck at the filesystem. I still find it somewhat odd that fsck cannot check xfs natively but I was able to run it via a live boot with xfs_check and xfs_repair.

The FS has no problem what so ever although both of my discs where found with 1 bad sector that wasn't there when the system was functioning. What can I say, I am pretty disappointed at this stage, most of my dist-upgrades with ubuntu have had issues, but I was always able to fix them. If bad sectors were created by this problem, then I might even switch distro :-(

---

