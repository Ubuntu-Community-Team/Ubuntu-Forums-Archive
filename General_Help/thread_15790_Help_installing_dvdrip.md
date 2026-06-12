---
title: "Help installing dvdrip"
date: 2005-02-16
forum: General Help
---

### Post by RadixLecti on 2005-02-16
Hello,

I've been trying to install dvdrip ([http://www.exit1.org/dvdrip/doc/gui-gui_burn.cipp](http://www.exit1.org/dvdrip/doc/gui-gui_burn.cipp)), and found out it's on the debian repositories (the ftp.nerim.net/debian-marillat ones).

Fine and dandy, I fire up synaptic and mark the file for download.
I get an error message: "Could not mark all packages for installation or upgrade. Depends: transcode but is not going to be installed."

Hmm, I think and search for transcode. There it is, I mark that for installation, thinking that might solve it. 

What I got was a new error message, wanting libdvdread2 this time, and saying it wasn't going to be installed. I have libdvdread3 installed, and can find no mention of libdvdread 2 anywhere in the repositories. Is this what fouled the installation up?

If I can't install this, is there another gui burner that can handle .bin/.cue, .img and other commonly used cd/dvd-image formats?

---

### Post by ups on 2005-02-17
Hi,

did u import marillat's GPG keys as instructed in the wiki?
[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)

---

### Post by ixus_123 on 2005-02-18
There is already a 2 page thread on this in this very forum.  It just takes a little time to search :)
[http://ubuntuforums.org/showthread.php?t=548](http://ubuntuforums.org/showthread.php?t=548) 

Transcode & DVDrip seem to throw up a lot of problems.  If it's just ripping DVDs to AVI you might want to try acidrip.  It's a perl frontend to Mencoder.

It works great but you can only have one soundtrack with it - one reason I'd like to get DVDrip working is so I can have more than one soundtrack

---

