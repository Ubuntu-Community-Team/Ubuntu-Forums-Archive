---
title: "Help! Ubuntu is screwed up because of maybe synaptic?"
date: 2009-10-26
forum: General Help
---

### Post by searchfgold6789 on 2009-10-26
Hi.

Whenever I try to run the flash 10 .deb installer, I et this error message:
>>>
**Software Index is Broken**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
>>>

Whenever I try to start Synaptic Package Manager, I get this error message:
>>>
**An Error occured**
The following details are provided:
E: Malformed 1st word in Status line
E: Error occurred while processing libpolkit-dbus2 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
>>>

And, when I try to start the Add/Remove Applications thing, I get *this* error message:
>>>
**Failed to check for installed and available applications**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
>>>
And there will be more soon. please help!
:(:(:(:(:(
 - Rich

---

### Post by arrrghhh on 2009-10-26
Post your /etc/apt/sources.list.  Also, try "'sudo apt-get update' and 'sudo apt-get install -f'" - post the output.

---

### Post by searchfgold6789 on 2009-10-26
Post what???
and, this is the output of those commands:

>>>
richie@richie-desktop:~$ sudo apt-get update
[sudo] password for richie: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [57.9kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [57.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [197kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [120kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2599B]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [31.4kB]         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [509B]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [61.9kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [14.9kB]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [1662B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [588B]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2599B] 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [55.4kB]       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [509B]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [83.2kB]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [23.6kB]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]  
Fetched 723kB in 17s (40.7kB/s)                                                
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libpolkit-dbus2 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
>>>
I hope that wasn't too much paste.


The result of the other one was:
>>>
richie@richie-desktop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing libpolkit-dbus2 (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
>>>

This did not fix any of the problems.

---

### Post by arrrghhh on 2009-10-26
I need you to post your /etc/apt/sources.list

Type "sudo gedit /etc/apt/sources.list"
Then hit "Ctrl-A" to select-all.
Copy and paste into this thread.

---

### Post by dj-toonz on 2009-10-27
or another way I've found to edit or check what's inside a file without opening it is this

less "name of the file" i.e in this case /etc/apt/sources.list > "where you want it copying to" /home/[username]/Desktop/"name of file" i.e Sources.txt

so that would be

less /etc/apt/sources.list > /home/"your_user_name"/Desktop/sources.txt

saves having to do the sudo before hand & then entering your password, then going to the file & opening it, cut's down on loads of commands

---

### Post by arrrghhh on 2009-10-27
That actually seems more complicated, but it really doesn't matter... I think there's something wrong with that file (it's where Ubuntu looks to download updates, patches, install software etc...)

---

### Post by searchfgold6789 on 2009-10-27
Allright, again, I hope i do not use to much paste. :lolflag:

I typed in the sudo thing, because the other one didn't work.
I got this result:

>>>
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
>>>

Hope this helps...

---

### Post by searchfgold6789 on 2009-10-27
Hello? anyone?
[-o<[-o<[-o<[-o<[-o<[-o<[-o<[-o<

---

### Post by philinux on 2009-10-27
Copy and paste this into a terminal. Post back the output.

```
cat /var/lib/dpkg/status | head -30
```

---

### Post by searchfgold6789 on 2009-10-27
Running out of paste
>>>
richie@richie-desktop:~$ cat /var/lib/dpkg/status | head -30
Package: libexempi3
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 748
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: exempi
Version: 2.0.2-2
Depends: libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1)
Description: library to parse XMP metadata (Library)
 Exempi is a library to parse XMP metadata as defined by the
 specification.
 .
 XMP (Extensible Metadata Platform) facilitates embedding metadata in files
 using a subset of RDF. Most notably XMP supports embedding metadata in PDF
 and many image formats, though it is designed to support nearly any file type.
Original-Maintainer: Asheesh Laroia <asheesh@asheesh.org>
Homepage: [http://libopenraw.freedesktop.org/wiki/Exempi](http://libopenraw.freedesktop.org/wiki/Exempi)

Package: libgtkspell0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 528
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: gtkspell
Version: 2.0.13-2
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.2), libcairo2 (>= 1.2.4), libenchant1c2a (>= 1.4.2), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.15.0), libpango1.0-0 (>= 1.22.0), zlib1g (>= 1:1.1.4)
>>>

That is the output of that command.

---

### Post by philinux on 2009-10-27
Use this.

```
sudo dpkg -P --force-depends libpolkit-dbus2 && sudo apt-get install -f
```

Make sure you use copy and paste.

Got this from here. [https://answers.launchpad.net/ubuntu/+question/8408](https://answers.launchpad.net/ubuntu/+question/8408)

I knew I'd seen this before.

---

### Post by arrrghhh on 2009-10-27
I thought I may have been barkin up the wrong tree with his sources.list, just couldn't think of anything else... but after I looked closer and saw that error, just didn't know what to do with it!  Nice fix.

---

