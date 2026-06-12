---
title: "Update error"
date: 2006-05-06
forum: General Help
---

### Post by Seth Williamson on 2006-05-06
For some time now, when I do an update, I get the following error message:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I keep getting this, day after day, although I altered nothing in my sources.list file.

Can somebody tell me what's going on here and how to fix it?

Seth Williamson
Slings Gap
Franklin County, VA
USA

---

### Post by Rog131 on 2006-05-06
Have you tried this ?: 
gzip trouble with apt-get update ([http://ubuntuforums.org/showthread.php?t=9944](http://ubuntuforums.org/showthread.php?t=9944)). 

xurizaemon's solution:

> Turned out that the client's proxy content filter (Dan's Firewall) was swapping in a pretty page that says "Access has been restricted, we don't recognise the extension .bz2". But (in deference to Microsoft's cleverness in implementing 'friendly error messages') the firewall doesn't return a 404 or other appropriate HTTP error code, it just serves up the exchanged content in place. BOO to that.

So, if you're getting inexplicably unable-to-be-decompressed files, try yanking the file and see if it looks like you're assuming it does. It might just be that the repositories, APT and all are fine, and something in between you and the repository is hosing things ...

Luckily, on account of their Incredible Firewall Setup, the simple fix was to switch to ftp:// URLs in the /etc/apt/sources.list file - bingo, no more silly proxy content filter.

---

