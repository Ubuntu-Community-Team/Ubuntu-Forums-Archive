---
title: "Ubuntu Install, 4 Partitions"
date: 2011-12-04
forum: General Help
---

### Post by slotdoctor on 2011-12-04
I want to thank you guys (I lost your names, the post I had printed is gone) for your most excellent discussion. For the last month I have been trying to install Ubuntu to reside alongside Win7. I was so frustrated with my inability to partition and install Ubuntu, that I send a Lenovo X-220 back to them. I purchased a Fujitsu P-771. Unfortunately, that did not work either. 

Then when I was about to give up I found your discussion, which I followed and was able to deal with the four (4) primary partitions and install Ubuntu on my Fujitsu P-771. I have not used Windows for the last six or seven years.

Again, thank you. I used win7 to resize the original C and D partitions. I also learned not to mess with the recovery and system partitions. With the free space I did as follows.

On windows, from start I

type diskpart

type list disk to find out unallocated disk space

type select disk X (X mean disk number)

type create partition extended

type create partition logic size=4000 (create swap)

type create partition logic size=12000 (create space for Ubuntu /Root)

type create partition logic size=24000 (created space for /home)


Restart windows and boot from Ubuntu CD

Select install Ubuntu

Select assign space Manually

Partition created for Ubuntu assign to "/"

Partition created for /home assign to "/home"

Start install process

Finish & reboot

This worked perfect. Thank you.

---

