---
title: "I cannot update, I keep getting this error. Please help!"
date: 2009-08-17
forum: General Help
---

### Post by Lavaeagle on 2009-08-17
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7AGPG error: [http://beagle-project.org](http://beagle-project.org) ./ Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://beagle-project.org/files/ubuntu/edgy/./Packages.bz2](http://beagle-project.org/files/ubuntu/edgy/./Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.


I keep getting this error, being new to ubuntu I don't know where to start.

---

### Post by jerrrys on 2009-08-17
go to

system>administration>software sources>third party;  then put a **# **mark in front of anything with [B]CD ROM
[/B]do this with the edit button.  the pubkey is a different thing, but do this first and post back the results

---

### Post by Lavaeagle on 2009-08-18
I did not see any CDROMs

---

### Post by jerrrys on 2009-08-18
two things

#1 is there a cd in your cd drive

#2 would you post a screenshot of authentications

EDIT

this beagle project is a edgy repository which had an end of life back in april 2009, why do you have this in your jaunty repo's?

---

### Post by HiImTye on 2009-08-18
uncheck your 'ppa.launchpad.net' and 'beagle-project.org' options from that list and try again

should fix your problem

---

### Post by Lavaeagle on 2009-08-18
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7AFailed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

This is the new error code.

---

### Post by theozzlives on 2009-08-18
Go to Ubuntu Software and uncheck your CDROM at the bottom.

---

### Post by ptsubin on 2009-08-18
Installing the keys from PPA will solve the error. This page explain the procedure,
[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

This will remove the GPG...

---

### Post by Lavaeagle on 2009-08-18
@ ptsubin:
I think this is the one that finally fixed it. tyvm!!
Thankyou every else who tried to help me!  This is what keeps this software alive!

---

