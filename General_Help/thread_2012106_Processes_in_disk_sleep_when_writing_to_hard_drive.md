---
title: "Processes in disk sleep when writing to hard drive"
date: 2012-06-28
forum: General Help
---

### Post by mkkyle on 2012-06-28
I recently did a fresh install of Kubuntu 12.04 on a new 64-bit system with 16GB RAM. However, when I run a program that involves a lot of sorting of datasets (reading and writing to the hard drive), almost all other active programs -- Firefox, Thunderbird, etc. -- go into "disk sleep" and things generally slow down, i.e. the mouse is slow to respond.

The sorting seems to take considerably longer on the new system than on what I was using before, Ubuntu 11.10 with half the RAM and a slower CPU. When this program (SAS) isn't running, things seem to be fine. When the program is not doing lots of read/write operations, it also seems fine.

The installation is on a 2TB drive. I thought it might be an issue with misaligned partitions, but I've checked them using parted from a livecd and they seem fine.

Is there something very obvious that I need to tweak?

---

### Post by zerubbabel on 2013-05-15
There was no response to this message, and no solution offered to others in the past that have asked about this "disk sleep" condition. I am hoping someone can shed some light on it, because I too am experiencing frequent mouse freeze-ups on one of my systems, which seem to coincide with processes going into this "disk sleep" state. Sometimes, in time, the mouse will wake up again, but usually it requires a system restart to recover. The system this is happening on is running Kubuntu 12.04, with all updates applied.

---

### Post by mkkyle on 2013-05-15
I can't really propose a solution or an explanation, but here is how I resolved this.

First, I installed 32-bit Ubuntu rather than 64-bit, even though I have a 64-bit system. No more disk sleep problems after that.

Eventually, I decided to give 64-bit another try. I did a fresh install of Ubuntu 12.04 LTS 64-bit, and haven't had the disk sleep problems since.

I also switched the installation to a new SSD, thinking that maybe the issue was the 2TB drive and its alignment. I didn't have the patience track down exactly what change was important.

---

### Post by zerubbabel on 2013-05-15
This system is running from a clean install of Kubuntu 12.04 LTS 64-bit. 

I didn't even consider the 32-bit version because it wouldn't support beyond 4 GB RAM. Hopefully that is not the only solution.

I wonder whether any of the newer kernels fix the problem...

---

### Post by zerubbabel on 2013-05-16
Bump...

---

