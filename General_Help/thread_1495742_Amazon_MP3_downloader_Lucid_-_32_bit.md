---
title: "Amazon MP3 downloader Lucid - 32 bit"
date: 2010-05-28
forum: General Help
---

### Post by MorrisseyJ on 2010-05-28
Hi, i am having some problems using Amazon's MP3 downloader in 32-bit Lucid.

I see that this has been dealt with here for 64 bit:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1392406](http://www.uluga.ubuntuforums.org/showthread.php?t=1392406)

And here:

[http://ubuntuforums.org/showpost.php?p=5522318&postcount=1](http://ubuntuforums.org/showpost.php?p=5522318&postcount=1)

Unfortunately neither works for me.

So far i have tried Clamz instructions from [http://ubuntuforums.org/showpost.php?p=5522318&postcount=1:](http://ubuntuforums.org/showpost.php?p=5522318&postcount=1:)

I do:
> sudo apt-get install libgcrypt11-dev libcurl4-openssl-dev libcurl4-openssl-dev libexpat1-dev
But when i do:
> 
tar -zxf clamz-0.1.tar.gz
I get this in the terminal:
> tar: clamz-0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
So i tried the instructions for using the MP3 downloader from Amazon, also from [http://ubuntuforums.org/showpost.php?p=5522318&postcount=1:](http://ubuntuforums.org/showpost.php?p=5522318&postcount=1:)

I start with:
> 
sudo apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
but i get:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost-signals1.34.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libboost-signals1.34.1 has no installation candidate
So it seems that there is still a problem with Lucid coming with  libboost-filesystem1.40.0. and not  libboost-filesystem1.34.1.

From [http://ubuntuforums.org/showthread.php?t=1392406&page=2](http://ubuntuforums.org/showthread.php?t=1392406&page=2) it seems that people got round this using the following script:
> #!/bin/sh[FONT=monospace]
[/FONT]sudo dpkg -i --force-all ~/amazonmp3.deb[FONT=monospace]
[/FONT]sudo apt-get install ia32-libs[FONT=monospace]
[/FONT]wget [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)[FONT=monospace]
[/FONT]sudo dpkg -i getlibs-all.deb[FONT=monospace]
[/FONT]sudo getlibs /usr/bin/amazonmp3sudo getlibs -p gvfs
sudo getlibs -w [http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb) [http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb) [http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb) [http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb) [http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb) [http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb) [http://ftp.osuosl.org/pub/ubuntu/pool/main/i/icu/libicu40_4.0.1-2ubuntu2_i386.deb](http://ftp.osuosl.org/pub/ubuntu/pool/main/i/icu/libicu40_4.0.1-2ubuntu2_i386.deb)
sudo ldconfig
My problem is that i am not sure what to do with this script. Where do i save it and how do i execute when i am trying to download a file? Sorry i still haven't worked out Linux.

If anyone can point me in the right direction in any of these problems that would be great. Ideally i'd like to use clamz but i'll use anything.

Thanks in advance.

---

### Post by Seamyst on 2010-05-29
Yes, I'd like to know how to do this, too.  Anyone?  Or should we contact Amazon directly, since it seems that they're still using an old dependency?

**Edit:**  Found the solution!  [The first post here]("http://ubuntuforums.org/showthread.php?t=1478214") gives great instructions - just paste each line one at a time into Terminal, then you can install the mp3 downloader as usual.

---

### Post by MorrisseyJ on 2010-05-30
Yup, thanks for that link. Worked perfectly. 

Anyone who fancies telling me what i just did there, that would be great.

---

### Post by Seamyst on 2010-05-30
As near as I can tell (someone please correct me if I'm wrong):

*mkdir old_boost* -- We're making a directory to house the stuff we're going to download.
*cd old_boost* -- We're going to the directory we just made.
*wget [https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb](https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb)* -- We're downloading several dependencies and/or files associated with the dependency we want.
*sudo dpkg -i *.deb* -- We're installing the dependencies we just downloaded.
*cd ..* -- We're going up a directory.
*rm -r old_boost* -- We're removing the directory we created at the beginning of the session, as it's no longer needed.

---

### Post by MorrisseyJ on 2010-05-30
Great, thanks. I think that makes sense.

---

### Post by pappo on 2010-08-29
> **Seamyst said:**
> As near as I can tell (someone please correct me if I'm wrong):

*mkdir old_boost* -- We're making a directory to house the stuff we're going to download.
*cd old_boost* -- We're going to the directory we just made.
*wget [https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959932/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959936/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959922/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959918/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959916/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb](https://launchpadlibrarian.net/26959928/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb) [https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb](https://launchpadlibrarian.net/34165098/libicu40_4.0.1-2ubuntu2_i386.deb)* -- We're downloading several dependencies and/or files associated with the dependency we want.
*sudo dpkg -i *.deb* -- We're installing the dependencies we just downloaded.
*cd ..* -- We're going up a directory.
*rm -r old_boost* -- We're removing the directory we created at the beginning of the session, as it's no longer needed.

When I do this it all works just fine.  But when I download and try to install the Amazon MP3 downloader.deb file ( which says it is for Ubuntu 9.04), I get this:

sudo dpkg -i *.deb

Selecting previously deselected package amazonmp3.
(Reading database ... 162426 files and directories currently installed.)
Unpacking amazonmp3 (from amazonmp3.deb) ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libglademm-2.4-1c2a; however:
  Package libglademm-2.4-1c2a is not installed.
 amazonmp3 depends on libboost-filesystem1.34.1; however:
  Package libboost-filesystem1.34.1 is not installed.
 amazonmp3 depends on libboost-regex1.34.1; however:
  Package libboost-regex1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 amazonmp3

Before I try to download all these dependencies, I thought I would check with some of you as to what is the best way to go forward.

---

### Post by MorrisseyJ on 2010-08-30
I am not certain about this (as i am no linux expert) but i am pretty sure that you'll need:

libboost-filesystem1.34.1

I don't know about:

libglademm-2.4-1c2a

I am not sure if anyone else can help.

---

### Post by Seamyst on 2010-08-30
It looks like you'll have to download and install those dependencies.  You should be able to do that from the Synaptic Package Manager or via the terminal, whichever you prefer.  Installing them can't hurt, anyway - and if you do encounter more problems, you can uninstall them just as easily.

---

### Post by pappo on 2010-08-30
> **Seamyst said:**
> It looks like you'll have to download and install those dependencies.  You should be able to do that from the Synaptic Package Manager or via the terminal, whichever you prefer.  Installing them can't hurt, anyway - and if you do encounter more problems, you can uninstall them just as easily.

Well, thanks to all for your comments.
It is too bad because this all worked fine in Ubuntu 9.04
Sad to say, but this Ubuntu 10.4 has given me more problems than any previous Ubuntu/Mint installs.

---

### Post by Seamyst on 2010-08-30
I've had to do more reconfiguring and finding workarounds than in previous versions, but once I got everything set up the first time, I haven't had any problems.

---

### Post by partofthething on 2010-09-04
Right, the Amazon program is looking for libraries that have been updated since Karmic. If you want a nice clean solution without touching the command line, here it is:

1) Add the karmic repository to software sources under system -> software sources by clicking the "other sources" tab, pressing add, and typing 
```
deb [http://ubuntu.secs.oakland.edu/ubuntu](http://ubuntu.secs.oakland.edu/ubuntu) karmic main universe 
```(or some other mirror). 

2) Then hit the reload button that pops up and let it reload the package info

3) Then close that and try to reinstall the package from the amazon website. It should find all the dependencies from the Karmic repos and all will work nicely. 

Hooray!

You might want to go back into software sources and uncheck the karmic repo after you do this install so you don't keep getting old packages. Not sure if this would be a problem but just to be safe I'm unchecking mine.

---

