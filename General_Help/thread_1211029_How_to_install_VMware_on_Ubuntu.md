---
title: "How to install VMware on Ubuntu"
date: 2009-07-12
forum: General Help
---

### Post by balumankala on 2009-07-12
Hello All
Im using Ubuntu Linux 9.04
I have downloaded VMware workstation for Linux 
Here is the file name "VMware-workstation-6.0.0-45731.i386.rpm"
Can someone let me know how do install this on Ubuntu

Thanks in advace
BALU

---

### Post by balumankala on 2009-07-12
Well, I have got some installation steps with the help of google
And im stuck at one point


It gives me the following error
> Unable to copy the source file ./installer/services.sh to the destination file 
/etc/vmware.

Execution aborted.

any idea how to over come this

---

### Post by Freezing on 2009-07-12
man rpm will give you nice info.

Install a package 
**rpm –ivh packagename** 
upgrade a package 
**rpm –Uvh packagename**

---

### Post by Gen2ly on 2009-07-12
Isn't there a .deb for this?

---

### Post by Legace on 2009-07-12
Why don't you get the .deb file instead of .rpm?

I would also suggest you give VirtualBox a try. I find it much better than VMWare. Fetch VirtualBox from virtualbox.org :)

---

### Post by balumankala on 2009-09-03
> **Freezing said:**
> man rpm will give you nice info.

Install a package 
**rpm &#8211;ivh packagename** 
upgrade a package 
**rpm &#8211;Uvh packagename**

When i give the above command, it gives the following output, not sure how to install thru rpm

> 
root@ubuntu:/home/balu/Desktop/VMware Linux/Linux_workstation6.part1# rpm &#8211;ivh VMware-workstation-6.0.0-45731.i386.rpm
RPM version 4.4.2.3
Copyright (C) 1998-2002 - Red Hat, Inc.
This program may be freely redistributed under the terms of the GNU GPL

Usage: rpm [-afgpWcdlsKiv?] [-a|--all] [-f|--file] [-g|--group] [-p|--package] [-W|--ftswalk] [--pkgid] [--hdrid] [--fileid]
        [--specfile] [--triggeredby] [--whatrequires] [--whatprovides] [--nomanifest] [-c|--configfiles] [-d|--docfiles] [--dump]
        [-l|--list] [--queryformat=QUERYFORMAT] [-s|--state] [--nomd5] [--nofiles] [--nodeps] [--noscript] [--comfollow] [--logical]
        [--nochdir] [--nostat] [--physical] [--seedot] [--xdev] [--whiteout] [--addsign] [-K|--checksig] [--delsign] [--import]
        [--resign] [--nodigest] [--nosignature] [--initdb] [--rebuilddb] [--aid] [--allfiles] [--allmatches] [--badreloc]
        [-e|--erase=<package>+] [--excludedocs] [--excludepath=<path>] [--fileconflicts] [--force] [-F|--freshen=<packagefile>+]
        [-h|--hash] [--ignorearch] [--ignoreos] [--ignoresize] [-i|--install] [--justdb] [--nodeps] [--nomd5] [--nocontexts]
        [--noorder] [--nosuggest] [--noscripts] [--notriggers] [--oldpackage] [--percent] [--prefix=<dir>] [--relocate=<old>=<new>]
        [--repackage] [--replacefiles] [--replacepkgs] [--test] [-U|--upgrade=<packagefile>+] [--quiet] [-D|--define='MACRO EXPR']
        [-E|--eval='EXPR'] [--macros=<FILE:...>] [--nodigest] [--nosignature] [--rcfile=<FILE:...>] [-r|--root=ROOT] [--querytags]
        [--showrc] [--quiet] [-v|--verbose] [--version] [-?|--help] [--usage] [--scripts] [--setperms] [--setugids] [--conflicts]
        [--obsoletes] [--provides] [--requires] [--info] [--changelog] [--xml] [--triggers] [--last] [--dupes] [--filesbypkg]
        [--fileclass] [--filecolor] [--filecontext] [--fscontext] [--recontext] [--fileprovide] [--filerequire] [--redhatprovides]
        [--redhatrequires] [--buildpolicy=<policy>] [--with=<option>] [--without=<option>]
root@ubuntu:/home/balu/Desktop/VMware Linux/Linux_workstation6.part1# 




---

### Post by P4man on 2009-09-03
rpm is for red hat linux,  you need a debian/ubuntu installer. Isnt there one?

Better yet, as someone else suggested, unless you got a specific reason to use VMWare, give VirtualBox a try

```
sudo apt-get install virtualbox
```

---

### Post by howefield on 2009-09-03
> **Gen2ly said:**
> Isn't there a .deb for this?

I don't think there is a .deb for this, but there is a .bundle which would be easier to install on Ubuntu than an rpm

Given the timeline in this thread, looks like the op is determined that it is rpm or nothing.....

---

### Post by louieb on 2009-09-03
Your ](*,) trying to install VMware with an RPM in Ubuntu. RPMs are for Red Hat/Fedora based distributions.  

Check the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") section of the forum - you'll find out how to install VMware in Ubuntu there. (see the 1st sticky)

---

