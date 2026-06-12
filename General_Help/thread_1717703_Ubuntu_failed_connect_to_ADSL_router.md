---
title: "Ubuntu failed connect to ADSL router"
date: 2011-03-30
forum: General Help
---

### Post by lumaja on 2011-03-30
After reinstall Ubuntu 10.04 LTS didn’t recognize my ADSL router Billion 400 G.
The Ethernet 1 led is off after booting.
Search on web for help on this but no good results.
You good people now are my last resort.
I tried boot in live CD and result is the some.
Check with sudo lshw.
uis@luis-desktop:~$ sudo lshw -c network 
[sudo] password for luis: 
*-network UNCLAIMED 
description: Ethernet controller 
product: AR8151 v1.0 Gigabit Ethernet 
vendor: Atheros Communications 
physical id: 0 
bus info: pci@0000:02:00.0 
version: c0 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress vpd bus_master cap_list 
configuration: latency=0 
resources: memory:fdec0000-fdefffff ioport:cf00(size=128) 
[EMAIL="luis@luis-desktop"]luis@luis-desktop[/EMAIL]:~$
Thank you

---

### Post by blueridgedog on 2011-03-30
Have you tested the cable or tried another cable?

What is the output of:

```
ifconfig
```

?

---

### Post by TBABill on 2011-03-30
Do you have multiple output ports on the router that you can try? And reseat the computer end of the cable? And try a different cable as mentioned above?
 
Since it's ADSL, do any other computers connect? Do you have a steady sync (sometimes called Ready) light?
 
Please give more details of exactly what you have tried, when it last worked, if other computers can connect, if you can connect in Windows but not Ubuntu, etc. Anything at all that could help diagnose.

---

### Post by lumaja on 2011-03-31
Firstly I am a novice in Ubuntu.
Result of ifconfig.
luis@luis-desktop:~$ ifconfig 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:112 errors:0 dropped:0 overruns:0 frame:0 
TX packets:112 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:8664 (8.6 KB) TX bytes:8664 (8.6 KB) 


[EMAIL="luis@luis-desktop"]luis@luis-desktop[/EMAIL]:~$
Yes there is multiple output ports, tried 1,2,3, same result ethernet lite is off.
I have two hard disks one with Ubuntu the other with Windows XP, ethernet can connect on Windows with no trouble, then disconnect the drive and connect Ubuntu drive the ethernet goes off and doesn’t came on after booting the reversal happens when changing to Windows.
I had Ubuntu and ADSL working with the same disk before, but I made a big mistake while changing password and couldn't get help to fix this,so with expenses of loosing all my data, I reinstall Ubuntu when I found it didn’t connect to router.
Examining this the only difference is on the first installation the hard disk it was a new one.
Both hard disks are Seagate ST3250318AS, thinking in format Ubuntu disk but Windows doesn’t see it and I don’t know how to format this disk to reinstall Ubuntu.
Please advise on this and if should.
Thank you for your response and try to help.
Regards

---

### Post by blueridgedog on 2011-03-31
It appears that the kernel has no module for your ethernet hardward.

This thread walks through installing a driver from the manufacture's web site:

[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

If you start the process, we can help if you get stuck.

---

### Post by dineshs on 2011-03-31
> *-network UNCLAIMED
description: Ethernet controller
product: AR8151 v1.0 Gigabit Ethernet
vendor: Atheros Communications Network unclaimed means a driver issue .Pl see
[http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential)

---

### Post by lumaja on 2011-04-01
As I understand Ubuntu needs a driver, but I cannot understand is why if Ubuntu before was working on this drive same computer with same mother board etc, the only change was the hard disk was new and not now, so the drive should be in the live CD the problem is now, why the installation dint find my Ethernet hardware. Please don’t take this wrongly I know your good people know much and much more that I do special about this animal UBUNTU, is just my logic.
Read every thing and I got very confused about all,went to : [http://partner.atheros.com/Dowload.aspx?id=125](http://partner.atheros.com/Dowload.aspx?id=125) and only driver with AR8151 is for windows.
I need help on how and where to download the drive and installation.
Please help me with this until completable.
Thank you

---

### Post by dineshs on 2011-04-01
> I need help on how and where to download the drive and installation.
[http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125)
click `accept' at the bottom of the page-click `back to driver downloads' on top of the pageand download AR81Family-linux-v1.0.1.14.tar.gz

---

### Post by lumaja on 2011-04-01
[FONT=Times New Roman][SIZE=3]I eventually found and downloaded the driver but the name doesn’t look right to me is Download.aspx., is this correct?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I f this is correct I need to know what should I do next.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thank you[/SIZE][/FONT]

---

### Post by dineshs on 2011-04-01
The file name is [COLOR="Red"]AR81Family-linux-v1.0.1.14.tar.gz[/COLOR]

---

### Post by lumaja on 2011-04-02
[FONT=Times New Roman][SIZE=3]Eventual I got the drive [/SIZE][/FONT][COLOR=red][FONT=Verdana]AR81Family-linux-v1.0.1.14.tar.gz[/FONT][/COLOR][FONT=Times New Roman][SIZE=3] in a USB driver, the fault was “FlashGet” downloading with different name, removing from Windows setup and then successful downloading in Windows.[/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Times New Roman]What should I do next?[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]You had been very patience with this and I thank you for it.[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]Regards[/SIZE][/FONT][/COLOR]

---

### Post by dineshs on 2011-04-03
You need to install build -essential first.Try this link
[http://ubuntuforums.org/showpost.php?p=9738022&postcount=7](http://ubuntuforums.org/showpost.php?p=9738022&postcount=7)
Then
> tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
cd src
sudo su
make install
modprobe atl1e
exit
Note: The first command will be in your case *tar zxvf AR81Family-linux-v1.0.1.14.tar.gz*

---

### Post by lumaja on 2011-04-04
Install from live CD.
Results of sudo apt-cdrom add. Doesn’t seem to be correct.


Just a reminder the download drivee is in USB drive.


To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 


luis@luis-desktop:~$ sudo apt-cdrom add 
[sudo] password for luis: 
Using CD-ROM mount point /media/apt/ 
Identifying.. [d00480f76f2d81dbf30817849c039fdc-2] 
Scanning disc for index files.. 
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures 
This disc is called: 
'Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)' 
Copying package lists...gpgv: Signature made Thu 29 Apr 2010 14:56:05 SAST using DSA key ID FBB75451 
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" 
Reading Package Indexes... Done 
Writing new source list 
Source list entries for this disc are: 
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted 
Repeat this process for the rest of the CDs in your set. 
W: Skipping nonexistent file /media/apt/dists/lucid/main/binary-i386/Packages 
W: Skipping nonexistent file /media/apt/dists/lucid/restricted/binary-i386/Packages 
luis@luis-desktop:~$ sudo apt-get update 
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid Release.gpg 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) lucid-updates Release.gpg 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_ZA 
Could not resolve 'za.archive.ubuntu.com' 
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg 
Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_ZA 
Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_ZA 
Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_ZA 
Could not resolve 'security.ubuntu.com' 
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_ZA 
Could not resolve 'security.ubuntu.com' 
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_ZA 
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_ZA 
Reading package lists... Done 
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_ZA.bz2](http://za.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_ZA.bz2) Could not resolve 'za.archive.ubuntu.com' 


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg) Could not resolve 'security.ubuntu.com' 


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_ZA.bz2) Could not resolve 'security.ubuntu.com' 


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_ZA.bz2) Could not resolve 'security.ubuntu.com' 


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_ZA.bz2) Could not resolve 'security.ubuntu.com' 


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_ZA.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_ZA.bz2) Could not resolve 'security.ubuntu.com' 


W: Some index files failed to download, they have been ignored, or old ones used instead. 
luis@luis-desktop:~$ sudo apt-get install build-essential 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
The following extra packages will be installed: 
dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch xz-utils 
Suggested packages: 
debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc 
libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc 
The following NEW packages will be installed: 
build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch xz-utils 
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/7,571kB of archives. 
After this operation, 24.6MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main g++-4.4 4.4.3-4ubuntu5 
File not found 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main g++ 4:4.4.3-1ubuntu1 
File not found 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main xz-utils 4.999.9beta+20091116-1 
File not found 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main patch 2.6-2ubuntu1 
File not found 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main dpkg-dev 1.15.5.6ubuntu4 
File not found 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main build-essential 11.4build1 
File not found 
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main fakeroot 1.14.4-1ubuntu1 
File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_i386.deb File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4_all.deb File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/b/build-essential/build-essential_11.4build1_i386.deb File not found 
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb File not found 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
luis@luis-desktop:~$

---

### Post by dineshs on 2011-04-06
To install build-essential pl try this
Go to system-administration-synaptic package manager and search build-essential
rightclick on build-essential then mark it  for installation.A list of packages/dependencies will be seen.Note down the file names 
or 
click mark-click on file-save markings as and save it somewhere.this will have the names
Download these packages seperately to a thumb drive via any other PC/OS and copy it to /var/cache/apt/archives.To open /var/cache/apt/archives run```
gksudo nautilus /var/cache/apt/archives 

```then copy from thumb drive and paste it .Now go to synaptic package manager,mark build-essential and apply.
Note:To download packages go to [packages.ubuntu.com]("packages.ubuntu.com") and select your distro

---

### Post by lumaja on 2011-04-06
Following your instruction I stop at “copy to /var/cache etc”.


[LEFT]Note:To download packages go to [packages.ubuntu.com]("http://packages.ubuntu.com/") and select your distro

[/LEFT]
what is **distro, **the version name? On this case (Lucid Lynx)
Sorry about this but I am raw in Ubuntu

---

### Post by dineshs on 2011-04-06
> what is distro, the version name? On this case (Lucid Lynx)Yes
Once you get the name of different packages download them all to a thumb drive(while downloading each,select the distribution as lucid) and copy to /var/cache/apt/archives (ie run [COLOR="Red"]gksudo nautilus /var/cache/apt/archives[/COLOR] and paste it

---

### Post by lumaja on 2011-04-08
I got the files for build-essential and install successfully, when start the installation I was asked to insert the disk labeled Ubuntu 10.04 LTS. Is this correct?
Later I went to terminal and copy from you Quote: “tar zxvf AR81Family-Linux-v1.0.1.14.tar
gz”.
luis@luis-desktop:~$ tar zxvf AR81Family-linux-v1.0.1.14.tar.gz 
tar: AR81Family-linux-v1.0.1.14.tar.gz: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Exiting with failure status due to previous errors 
luis@luis-desktop:~$ 
I don’t understand this, I see so many threads successfully resolved the same way.

---

### Post by dineshs on 2011-04-08
> luis@luis-desktop:~$ tar zxvf AR81Family-linux-v1.0.1.14.tar.gz
tar: AR81Family-linux-v1.0.1.14.tar.gz: Cannot open: No such file or directory  The file AR81Family-linux-v1.0.1.14.tar.gz should be in home folder when you try this.If it is on desktop you need to change your directory by running *cd Desktop*.To avoid confusion just try the following steps 
Copy AR81Family-linux-v1.0.1.14.tar.gz to your home folder and run
> mkdir AR81Family
mv AR81Family-linux-v1.0.1.14.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-linux-v1.0.1.14.tar.gz
sudo su
make install
modprobe atl1e
exit
Reference to chili555 s post:[http://ubuntuforums.org/showpost.php?p=9257690&postcount=6](http://ubuntuforums.org/showpost.php?p=9257690&postcount=6) which also says linux-headers-generic need be installed as explained [here]("http://ubuntuforums.org/showpost.php?p=10648894&postcount=22")

---

### Post by lumaja on 2011-04-11
[FONT=Times New Roman][SIZE=3]I open Home and Desktop directories but the file “AR81Family” is not on either, in Desktop there is a file with the names of the packages that had to be downloaded and nothing else. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]How I understand your last instruction, I have to copy the file to home folder but I don’t know where the file is and then execute the Quote.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please help me further to correct this.[/SIZE][/FONT]
[FONT=Times New Roman]Thank you[/FONT]

---

### Post by jerome1232 on 2011-04-11
You need to [Click Here]("http://partner.atheros.com/Download.aspx?id=162")

and accept their license agreement. Copy the downloaded file to the home folder of your ubuntu box then proceed with previous instructions.

---

### Post by lumaja on 2011-04-11
[FONT=Times New Roman][SIZE=3]TO Dineshs[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I download the file again and drop in home folder [/SIZE][/FONT][COLOR=black][FONT=Verdana]then execute your quote. Result follows.[/FONT][/COLOR]
[FONT=Verdana][EMAIL="luis@luis-desktop:~$"]luis@luis-desktop:~$[/EMAIL] mkdir AR81Family [/FONT]
[FONT=Times New Roman][SIZE=3]mkdir: cannot create directory `AR81Family': File exists [/SIZE][/FONT]
[EMAIL="luis@luis-desktop:~$"][FONT=Times New Roman][SIZE=3]luis@luis-desktop:~$[/SIZE][/FONT][/EMAIL]
[FONT=Times New Roman][SIZE=3]I am getting more and more confused of this.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]TO jerome1232[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thank you for the hint I did just that.[/SIZE][/FONT]

---

### Post by dineshs on 2011-04-12
> mkdir: cannot create directory `AR81Family': File exists means such a folder is already there
try> mv AR81Family-linux-v1.0.1.14.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-linux-v1.0.1.14.tar.gz
sudo su
make install
modprobe atl1e
exit 

---

### Post by lumaja on 2011-04-12
[FONT=Times New Roman][SIZE=3]Dineshs I have to apologize for the error that I made. I should gone and look home folder because of “AR81Family: File exists and I didn’t. After wrote my lost post went to Ubuntu again as I notice my error I tried to fix it and I did this delete the file and copy it to home folder and execute your quote, since then I received your last post, but first follows the result of my correction and waiting for feedback.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Rebooting the Ethernet 1 still doesn’t come on meaning there isn’t connection between Ubuntu and router.[/SIZE][/FONT]
[FONT=Verdana]luis@luis-desktop:~$ mkdir AR81Family [/FONT]
[FONT=Times New Roman][SIZE=3]luis@luis-desktop:~$ mv AR81Family-linux-v1.0.1.14.tar.gz AR81Family [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]luis@luis-desktop:~$ cd AR81Family [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]luis@luis-desktop:~/AR81Family$ tar zxvf AR81Family-linux-v1.0.1.14.tar.gz [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./ [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./atl1e.7 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./atl1e.spec [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./at_osdep.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./copying [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./dkms.conf [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./ldistrib.txt [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./Makefile [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./pci.updates [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./readme [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./release_note.txt [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/ [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/.atl1c_main.c.swo [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1c.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1c_ethtool.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1c_hw.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1c_hw.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1c_main.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1c_param.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1e.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1e_ethtool.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1e_hw.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1e_hw.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1e_main.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/atl1e_param.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/at_common.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/at_common_main.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/at_osdep.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/kcompat.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/kcompat.h [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gzip: stdin: decompression OK, trailing garbage ignored [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/kcompat_ethtool.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/Makefile [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/Module.markers [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/Module.symvers [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]./src/modules.order [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]tar: Child returned status 2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]tar: Exiting with failure status due to previous errors [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]luis@luis-desktop:~/AR81Family$ sudo su [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password for luis: [/SIZE][/FONT]
[FONT=Times New Roman]root@luis-desktop:/home/luis/AR81Family#     [/FONT]

---

### Post by dineshs on 2011-04-12
Please proceed

---

### Post by lumaja on 2011-04-13
[FONT=Times New Roman][SIZE=3]I proceed with "[/SIZE][/FONT][COLOR=black][FONT=Verdana]mv AR81Family-linux-v1.0.1.14.tar.gz AR81Family", the first entry gave a error.[/FONT][/COLOR]
[SIZE=3][FONT=Arial Unicode MS]luis@luis-desktop:~$ mv AR81Family-linux-v1.0.1.14.tar.gz AR81Family [/FONT][/SIZE]
[SIZE=3][FONT=Arial Unicode MS]mv: cannot stat `AR81Family-linux-v1.0.1.14.tar.gz': No such file or directory [/FONT][/SIZE]
[EMAIL="luis@luis-desktop:~$"][FONT=Arial Unicode MS][SIZE=3]luis@luis-desktop:~$[/SIZE][/FONT][/EMAIL]
[SIZE=3][FONT=Arial Unicode MS]Thank you  [/FONT][/SIZE]

---

### Post by dineshs on 2011-04-13
Do all steps one by one
```
cd AR81Family
sudo su
make install
modprobe atl1e
exit 
```
> luis@luis-desktop:~$ mv AR81Family-linux-v1.0.1.14.tar.gz AR81Family
mv: cannot stat `AR81Family-linux-v1.0.1.14.tar.gz': No such file or directory Reason for the error was you have already moved AR81Family-linux-v1.0.1.14.tar.gz in home folder to  AR81Family there.

---

### Post by lumaja on 2011-04-14
**[FONT=Times New Roman]It is working.[/FONT]**
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Router is working and I can connect to the web.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Dineshs, thank you very much for this great help and patience, I am sorry for my mistakes.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I am going to make another question I which you read it, you might have the answer.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Regards [/SIZE][/FONT]

---

### Post by jerome1232 on 2011-04-14
Minor thing but it is recomended to use sudo -i to get an interactive root shell instead of sudo su.

sudo su (from my understanding) keeps some of your users environment options and has the possibility of getting some of your users (config) files accidentally owned by root.

sudo -i simulates an initil login as root and does not have the same issue as sudo su or sudo -u which do not pull in roots profile.

---

### Post by dineshs on 2011-04-14
> Dineshs, thank you very much for this great help and patience, I am sorry for my mistakes.Glad you got it working.Thanks to chili555 for posting [this]("http://ubuntuforums.org/showpost.php?p=9257690&postcount=6")
Thanks to jerome1232 too.

---

### Post by blueridgedog on 2011-04-15
Excellent work dineshs...tough to build without internet access.

On an unrelated note...it certainly would be nice to have a build environment out of the box with an Ubuntu install.

---

### Post by lumaja on 2011-05-04
[COLOR=black][FONT=Times New Roman][SIZE=3]Thank you dineshs  and others for your great help.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]As i was expecting it happen again, now i don’t know if to write[/SIZE][/FONT][/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR][COLOR=black][FONT=Times New Roman][SIZE=3]new thread or just carry on with this one. One more thing how to mark SOLVED.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]Regards[/SIZE][/FONT][/COLOR]

---

### Post by jerome1232 on 2011-05-04
It is marked solved and what exactly happened? Did you update to a new kernel? I believe you would just need to recompile it again. Every time there's a kernel update you would need to do that.

---

### Post by lumaja on 2011-05-05
[FONT=Times New Roman][SIZE=3]I dint know it was solved is not showing on the site.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]After been fixed i had the feeling will happen again. This come from after download Ubuntu UPDATES, which was over 200MG and exactly what happen before, i notice there was updates for Firefox, might be this the cause or there is something wrong with Ubuntu, tried other Ubuntu version before and never had this problem. The router loses connection with computer; the ethernet led (light) is off after the download and rebooting Ubuntu. My problem now is do i have to go throw this every time after updating?.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Do I have to download all the files on the update list?.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Regards[/SIZE][/FONT]

---

### Post by jerome1232 on 2011-05-05
Your right it must have been another post that I saw was marked solved, just click thread tools and mark as solved.


A firefox update wouldn't be the cause, more likely a kernel update, and yes you would need to recompile the drivers anytime a kernel update occurs.

---

### Post by lumaja on 2011-05-06
[FONT=Times New Roman][SIZE=3]Sorry to insist on this on.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]On my point of view it’s very bad news.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I wanted to leave windows. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]It’s unbelievable they don’t fix this, this 10.04 LTS is the latest.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ubuntu updates do they [/SIZE][/FONT][COLOR=black][FONT=Verdana]update the kernel[/FONT][/COLOR][FONT=Times New Roman][SIZE=3] always?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Is this error with every one using this version?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Is the cause my new mother board (Gigabyte G41-Combo)?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Did any of you clever people out there let Ubuntu know and to make urgently a fix?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Regards[/SIZE][/FONT]

---

### Post by jerome1232 on 2011-05-06
Your network card drivers for whatever reason are not included in the kernel by default, so you have to compile them yourself.

Anytime you have a self compiled driver it is for the specific kernel that you were running, when you upgrade your kernel (which occurs with some updates, just watch them to see if there is a kernel update) then you have to recompile them at next boot.

So in answer to your questions.

> It’s unbelievable they don’t fix this, this 10.04 LTS is the latest.

It's the latest LTS, but 10.10 and 11.04 (non LTS) are newer than 10.04.

> Is this error with every one using this version?

It's not an error, it's just how it is, if you self compile drivers you have to re-do it anytime there is a kernel update. It's possible your card is included in a newer kernel that would come with the newer versions of Ubuntu, you'd have to check into that.

> Is the cause my new mother board (Gigabyte G41-Combo)?

Sort of, the ethernet controller on your mother board isn't supported by default by Ubuntu. I don't know why it's not included, I could do a little digging on it.

---

### Post by lumaja on 2011-05-13
[FONT=Times New Roman][SIZE=3]Jerome1232 I apologize for not answer early, I been away.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The router is connected and working, your explanation is very good in an understanding way I thank you very much for it and if could find more about it will be appreciated.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Can you send email to me?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Regards[/SIZE][/FONT]

---

