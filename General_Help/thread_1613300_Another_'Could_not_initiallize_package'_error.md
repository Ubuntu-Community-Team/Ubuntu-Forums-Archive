---
title: "Another 'Could not initiallize package' error"
date: 2010-11-04
forum: General Help
---

### Post by Tunnelrat81 on 2010-11-04
Running Maverick via USB flash card on an HP Laptop.  I'm up and running, but had a few things to install/setup in order to get things usable.  All was well until last night when I did a couple installs and...now when I boot up, it gets to the desktop and lags forever...before finally showing the desktop icons and giving me a mouse.  

Also, I'm also completely locked out of anything having to do with Software management, Synaptic, or manual apt-get. 

The installations that I did last night involved openjdk-6-jdk, and adobe flash.  Was also trying to install wpa_supplicant, but I think that's what lead me to the openjdk if I'm remembering correctly.  Feel free to correct me on this.

I'm getting the above "thread title" error upon opening any gui package manager followed by :

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/Ubuntu%2010.10%20%5fMaverick%20Meerkat%5f%20-%20Release%20i386%20(20101007)_dists_maverick_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I did some searching around that offered the suggestion to

sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update

But when I remove the lists I get errors at the end for printouts that some lines cannot be removed...which means the problem persists.  

Also, following my "sudo apt-get update" readout is this:

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Syntax error /var/lib/apt/cdroms.list:110: Extra junk after value

E: Some index files failed to download, they have been ignored, or old ones used instead.

When I open that list file with gedit, it's enormous and I don't know how to find or correct any syntax errors...so I'm stuck.

I'll have time to work on this later tonight, but would love any suggestions for resolving this.  

-Jeremy

---

