---
title: "How can I change the volume label on DVD ISO's?"
date: 2010-11-17
forum: General Help
---

### Post by FatalKeystroke on 2010-11-17
I make duplicates of all my DVD's and keep the originals stored in boxes in my basement. I have a program I wrote that copies and ISO of the DVD, extracts it, adds some special metadata I use for my computer/media center to recognize exactly what movie it is and then puts it back into an ISO.
I have the slight problem that I want to change the disk label on some of the disks so that they make sense and fit some sort of standard. i.e. change "INNOCENT_BLOOD_4X3_FF_BUDGET" into "Innocent Blood [1992]"

Does anyone know a tool in that will allow me to do this? Preferably something that has a command line interface if possible.

---

### Post by sammingo on 2012-02-18
I had this same problem and [asked the question on serverfault.com]("http://serverfault.com/q/361474/2518"). Someone had a method which worked for me. It requires creating a Perl script but it's about the simplest script you'll ever have to make. The code is included in the answer to my quesiton at this link: [http://serverfault.com/a/361479/2518]("http://serverfault.com/a/361479/2518")

Here's the code as well:
```

#!/usr/bin/perl
use strict;
use warnings;

die "Use: $0 <iso_file> <new volume id>\n" unless @ARGV == 2;
open my $file, "+<", $ARGV[0] or die "Cannot open: $!";
seek $file, 0x8028,0;
printf $file "%-32.32s", uc($ARGV[1]);

```

You can use isoinfo to see what a .iso files Volume ID is like so:

```

% isoinfo -d -i /usr/share/virtualbox/VBoxGuestAdditions.iso 
CD-ROM is in ISO 9660 format
System id: Win32
Volume id: VBOXADDITIONS_4.1.8_75467
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 22203
Joliet with UCS level 3 found
Rock Ridge signatures version 1 found

```

---

