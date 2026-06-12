---
title: "Apt-get from USB install &lt;no internet&gt; Ubuntu 11.10"
date: 2012-03-01
forum: General Help
---

### Post by RHub787 on 2012-03-01
I installed Ubuntu 11.10 (Oneiric) from a bootable USB drive.  The installation went smoothly.  Ubuntu, however did not detect my wireless card which has the T.I. ACX 100 chipset.

I found a thread here in the forums for "a patch to compile acx 100/111 driver in kernel 2.6.31"

This patch requires the build-essential package, unfortunately I cannot seem to get Apt-get working to install build-essential.  Ubuntu seems to be looking for the package in the installation CD.(Which I don't have)

These are the steps I've taken so far to attempt to fix this problem:

1. Log in as root

2. Created a directory named ***repositories*** in */home*

3. Copied all files from the bootable USB to */home/repositories *

4. Used the Software Sources application to add new repository > deb file:///home/repositories oneiric main restricted5. Open Terminal

6. apt-get update

7. apt-get install build-essential

results:
> 
rob@rob-buntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libtimedate-perl
Suggested packages:
  debian-keyring g++-multilib
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libtimedate-perl
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 852 kB of archives.
After this operation, 3,850 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main g++ i386 4:4.6.1-2ubuntu5
  Could not resolve 'archive.ubuntu.com'
Err file:/home/repositories/ oneiric/main g++ i386 4:4.6.1-2ubuntu5
  File not found
Err file:/home/repositories/ oneiric/main libtimedate-perl all 1.2000-1
  File not found
Err file:/home/repositories/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5
  File not found
Err file:/home/repositories/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5
  File not found
Err file:/home/repositories/ oneiric/main build-essential i386 11.5ubuntu1
  File not found
Err file:/home/repositories/ oneiric/main libalgorithm-diff-perl all 1.19.02-2
  File not found
Err file:/home/repositories/ oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1
  File not found
Err file:/home/repositories/ oneiric/main libalgorithm-merge-perl all 0.08-2
  File not found
Failed to fetch file:///home/repositories/pool/main/g/gcc-defaults/g++_4.6.1-2ubuntu5_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/libdpkg-perl_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/dpkg-dev_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/b/build-essential/build-essential_11.5ubuntu1_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-2_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-1build1_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?***The USB installation went smoothly and the .iso checksum matches up.
Any ideas are greatly appreciated.  Thanks!

---

### Post by jerrrys on 2012-03-01
To be clear; you have internet access from your ubuntu install, right??  And you are putting a sudo in front of the apt-get commands?  like sudo apt-get update

And I don't understand your method of handling repositories.  So how bout (in terminal) posting the output of:

cat -n /etc/apt/sources.list

---

### Post by RHub787 on 2012-03-02
Hey Jerrys, sorry to get back so late.

Negative, there is no internet on Ubuntu.  I have a dual boot with WinXP on a separate partition.  Right now I am using puppy linux for internet access.  

yes I am using sudo.

cat -n /etc/apt/sources.list
> rob@rob-buntu:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted #Added by software-properties
     3	
     4	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     5	# newer versions of the distribution.
     6	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
     7	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main multiverse universe #Added by software-properties
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
    12	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates restricted main multiverse universe #Added by software-properties
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team. Also, please note that software in universe WILL NOT receive any
    16	## review or updates from the Ubuntu security team.
    17	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
    18	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
    26	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
    27	
    28	## N.B. software from this repository may not have been tested as
    29	## extensively as that contained in the main release, although it includes
    30	## newer versions of some applications which may provide useful features.
    31	## Also, please note that software in backports WILL NOT receive any review
    32	## or updates from the Ubuntu security team.
    33	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse
    34	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-backports main restricted universe multiverse #Added by software-properties
    35	
    36	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
    37	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
    38	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
    39	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    46	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    47	
    48	## This software is not part of Ubuntu, but is offered by third-party
    49	## developers who want to ship their latest software.
    50	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    51	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    52	deb file:///home/repositories oneiric main restricted
    53	deb-src file:///home/repositories oneiric main restricted

---

### Post by RHub787 on 2012-03-02
I should also mention I followed the instructions from here:

[https://help.ubuntu.com/community/AptGet/Offline/Repository]("https://help.ubuntu.com/community/AptGet/Offline/Repository")

with now avail

---

### Post by jerrrys on 2012-03-03
4. Used the Software Sources application to add new repository      Quote:
                                                 deb file:///home/repositories oneiric main restricted

remove that.

your sources.list should look something like this:

[https://help.ubuntu.com/11.10/serverguide/sample/sources.list](https://help.ubuntu.com/11.10/serverguide/sample/sources.list)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+sources+list&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+sources+list&sa=Search&cof=FORID:9)

The easy way (for the moment) would be to plug into (hard wire) the internet.

Edit:  I forgot.  What kind of graphics you got?  In terminal:
[FONT=monospace]
[/FONT]lspci -nn | grep VGA

and/or

sudo lshw -C display

---

### Post by RHub787 on 2012-03-03
Thanks for the help!  I got it working!

I looked at 

> Failed to fetch file:///home/repositories/pool/main/g/gcc-defaults/g++_4.6.1-2ubuntu5_i386.deb  File not found
Failed to fetch file:///home/repositories/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/libdpkg-perl_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/d/dpkg/dpkg-dev_1.16.0.3ubuntu5_all.deb  File not found
Failed to fetch file:///home/repositories/pool/main/b/build-essential/build-essential_11.5ubuntu1_i386.deb  File not found
Failed to fetch  file:///home/repositories/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-2_all.deb   File not found
Failed to fetch  file:///home/repositories/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-1build1_i386.deb   File not found
Failed to fetch  file:///home/repositories/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb   File not foundand got all the .DEB packages from the online repos, and maually placed them in the right directories, and WALA!

Now I have build-essential, but there is still a problem adding my wireless card acx 100 driver,  I think I'll start another thread for that.

---

