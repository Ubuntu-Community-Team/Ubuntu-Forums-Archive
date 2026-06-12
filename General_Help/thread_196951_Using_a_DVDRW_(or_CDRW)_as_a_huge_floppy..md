---
title: "Using a DVDRW (or CDRW) as a huge floppy."
date: 2006-06-15
forum: General Help
---

### Post by Fred Doolie on 2006-06-15
Can it be done in Ubuntu? Winblows has INCD. Linux must have something.

---

### Post by blackjack6.21.91 on 2006-06-15
bump

---

### Post by scxtt on 2006-06-15
in what way are you trying to use optical media as a floppy?

---

### Post by Fred Doolie on 2006-06-15
The CDRW (DVDRW) would act like a huge floppy (or little HDD whichever you prefer). I use to do that in windoze. Copy a file to it and the file was written. Delete a file and the space would be freed up.  It was nice for my collections of pictures and stuff.

---

### Post by scxtt on 2006-06-15
so you want to read/write a CD-RW / DVD±RW in Ubuntu as if it was a hard drive?

---

### Post by Ramses de Norre on 2006-06-15
You'll need to use a udf filesystem on the disc instead of the default iso9660, there is a package "udftools" in the repos but I don't know what exactely is included. Try it out and let us know I'd say=)

---

### Post by meatbop on 2006-06-15
Packet writing is [apparently]("http://reactivated.net/software/packetwriting/") supported in the kernel

Haven't tried this myself, and I couldn't find anything specific to Ubuntu or Debian, but here are instructions for Fedora Core and Mepis, might point you in the right direction.

[http://www.raoul.shacknet.nu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/](http://www.raoul.shacknet.nu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/)
[http://www.mepis.org/node/5612](http://www.mepis.org/node/5612)

On a cautionary note, packet written CD's may be less compatable with other machines than normal ISO CD's.  A friend of mine got burned a few years back using Easy CD Creator's packet writing tool.  He lost the disk the utility was on, a newer and non backward compatable version was out and he was never able to find a copy of the version he used to create a number of disks.

He didn't lose anything important, but the potential was there.

---

### Post by Irony on 2006-06-15
I've wondered this for a long time as I use DVD+RW discs in windows all the time with InCD - udftools looks like a promising option.

---

### Post by jis on 2006-07-17
I am afraid you can't read the discs formatted by InCD in linux, unless you have created them with Mt Rainier option selected. (Some versions of InCD support Mt. Rainier format.)

See [http://en.wikipedia.org/wiki/CD-MRW](http://en.wikipedia.org/wiki/CD-MRW) about Mount Rainier Packet Writing. 

If you have A Mount Rainier-compliant drive, you might want to read [http://www.thehaus.net/AltOS/Linux/ht-mtrainier.shtml](http://www.thehaus.net/AltOS/Linux/ht-mtrainier.shtml) about Mount Rainier Support in Linux. Would anybody more experienced with ubuntu linux be so kind and tell more specifically, how to "enable" the Mt. Rainier support in ubuntu. Especially, do I have to download linux kernel source? (Chapter "Compile the Tools" seems to tell implicitely that I should have kernel sources. On the other hand, I can't find the source code of exactly the same kernel version that I am using in the repositories - namely "2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux" as given by "uname -a" command.) I also wonder, if I can just install the udftools from Synaptic Package Manager; what do I need the source of udftools for?

---

### Post by jis on 2006-08-20
I also have succeeded to use the Mt. Rainier feature in (X)ubuntu by a Mt. Rainier compliant drive. The instructions are at [http://www.thehaus.net/AltOS/Linux/ht-mtrainier.shtml](http://www.thehaus.net/AltOS/Linux/ht-mtrainier.shtml) but I did not want to install all ubuntu source to compile cdmrw.c. I compiled like this instead: I installed linux-headers package that match kernel version (that can be checked by uname -r). BTW Do I have to recompile after possible kernel update? I also installed
gcc and build-essential packages, downloaded cdmrw.c
to Desktop and ran 

gcc cdmrw.c -o cdmrw
-I/usr/src/linux-headers-*/include

where * is your kernel version; for me it was 2.6.15-23-386. Compiler gave some warnings, however; see the attachment. How can I get rid of those warnings and should I care about them? I installed udftools from repository so I did not have to compile it.

I found that, unlike I thought, you can read conventional InCD discs if you mount the disc as udf type and read-only.

Can I read cd-mrw discs by a drive that is not Mt. Rainier compliant in linux? (For Windows there is an application for that purpose, namely  InCD4Reader.exe at [http://ww2.nero.com/nero6/eng/Support_Tools_InCD_4_Reader.html](http://ww2.nero.com/nero6/eng/Support_Tools_InCD_4_Reader.html))

P.S. I just found out that the compiler warnings can be avoided by adding #include <string.h> to the source file. This is maybe because the compiler is not backwards compatible with the one used originally for compiling. The binary stayed same anyway.

---

