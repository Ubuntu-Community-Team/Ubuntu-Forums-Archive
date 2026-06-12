---
title: "Question about RAM"
date: 2009-07-12
forum: General Help
---

### Post by shelbyvision on 2009-07-12
Since I've been having some major problems, (see my other thread,
[http://ubuntuforums.org/showthread.php?t=1209456]("http://ubuntuforums.org/showthread.php?t=1209456")), I've been checking into various things, like my computer's RAM. I made some puzzling discoveries. I have 512 MB of RAM installed. When I looked in my BIOS in setup, it shows 522240 KB, which calculates to only 510 MB. When I check memory in the system monitor, it shows "502.5 MiB". Shouldn't both ot those numbers be 512? Is my RAM degrading? Please enlighten me.
Thank you,
Steve

---

### Post by lordofallhearts on 2009-07-12
Maybe your BIOS uses 2MB and OS uses more of it to upload its applications

---

### Post by TeamJ on 2009-07-12
1 byte=8 bits

1 Kibibyte (KiB)=1000bytes
1 MibiByte (MiB)=1000Kibibytes
1 Gibibyte (GiB)=1000Mibibytes

etc.

1 Kilobyte (Kb)=1024bytes
1 Megabyte (Mb)=1024Kilobytes
1 Gigabyte (Gb)=1024Megabytes

etc.

some people get this confused and are therefore innaccurate

---

### Post by GCoffee on 2009-07-12
It's perfectly possible that your BIOS & OS use diffrent amounts of RAM to run.

Because the OS needs more resources it will take more RAM to run, unlike the BIOS, which only needs a small amount to run.

---

### Post by shelbyvision on 2009-07-12
Thanks, everyone, for the information. 
I never heard of kibibytes or mibibytes, etc. before. Is that only used in the Linux world? Actually it makes much more sense, like the metric system.
I guess I had the wrong idea about RAM. I thought it was only being used when the computer was computing, but not when it was just sitting there.
So, I guess I can surmise by your answers that there is probably nothing wrong with my computer's RAM, and the problem it has is something else.
Steve

---

### Post by TeamJ on 2009-07-12
each type has its qualities, 1024 is more mathematcally useful, and is in a sort of grouping where it is doubled. it is present in Ram as well as HDDs and screen resolution
1
2
4
8
16
32
64
128
256
512
1024
2048
4096
8192

etc. quite a lot of those numbers are familiar

---

