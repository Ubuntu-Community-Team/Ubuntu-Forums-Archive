---
title: "Error with burning data DVD+R"
date: 2011-01-12
forum: General Help
---

### Post by Flexico on 2011-01-12
I don't know what the difference is between DVD+R and DVD-R or if it matters, lol.

I was trying to burn 2.0 GB of data to a 4.7-GB DVD+R and after it finished burning, I got "There was an error writing to the disk."

When I opened the directory of the disk, it appeared that all of the files were there, but when I tried to open any of them, I got "Could not read from the resource" errors.

I tried burning it again to a fresh disk and it was the same except when I tried to open the files it said variations of "error interpreting file".

I checked the log files and mostly it was unhelpfully generic errors, except for this line:
"BraseroLibburn Asynchronous SCSI error on CLOSE TRACK SESSION: [3 73 04] Program memory area update failure"

That part was the same for both attempts. What could be causing this?

---

### Post by Quackers on 2011-01-12
Have you installed ubuntu-restricted-extras or in particular the dvd+rw package. They may make a difference.

---

### Post by mc4man on 2011-01-12
It may be the disk wasn't finalized.
Personally don't use brasero though have tested with mainly success. However when it does fail the error messages aren't that all helpful (at least to 'common' folk

You may wish to try switching to cdrecord amd mkiosfs instead of the default wodim and genisoimage

If so add this ppa and reload your sources
[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

Then open synaptic - search cdr and _just mark cdrecord and mkisofs for install_
(wodim and genisoimage will be automatically removed and cdrecord and mkisofs will take their place as far as apps that depended on and used them.

---

