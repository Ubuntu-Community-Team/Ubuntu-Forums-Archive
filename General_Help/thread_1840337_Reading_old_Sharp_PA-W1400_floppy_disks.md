---
title: "Reading old Sharp PA-W1400 floppy disks"
date: 2011-09-07
forum: General Help
---

### Post by Paul Crawford on 2011-09-07
I have been trying to read and convert files from some floppy disks that my father accumulated over the years for his "word processor". I have had some success with this and made the code & method public here:

[http://www.sat.dundee.ac.uk/~psc/sharp-pa-w1400/sharp.html](http://www.sat.dundee.ac.uk/~psc/sharp-pa-w1400/sharp.html)

However, the process of getting files off the disks is far from easy as I find the majority won't mount in either Windows or Linux due to them having an old (and possibly incomplete) FAT12 system.

I have used a DOS 6.22 virtual machine, but even that was corrupted at one point (maybe due to flaky file access). Also that is 'licensed' so I am not free to distribute it.

Has anyone got any idea of finding a Linux method to get the files off?

It has to work with the physical disk (as the OS won't mount most of them to simply read /media/floppy), but could work with an image file (but much more hassle for anyone doing so, and 'dd' is potentially dangerous in unskilled/careless hands, so would have to be automated).

Also has anyone got any example files with known text using accented characters to help improve the format conversion code?

---

