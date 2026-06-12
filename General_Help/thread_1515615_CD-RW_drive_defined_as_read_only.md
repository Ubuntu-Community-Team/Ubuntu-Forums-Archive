---
title: "CD-RW drive defined as read only"
date: 2010-06-22
forum: General Help
---

### Post by Rogierdg on 2010-06-22
I have Ubuntu 10.04 installed on an Armada laptop with a Teac CD-W24E installed.
This drive can handle cd, cd-r and cd-rw, however the cd/dvd writer and hence Brasero detects it as **read only**. So no possibility to write!!
Also, when I load a blank disk the cd drive icon disapears from the file browser page .  The disk utility program detects the loaded empty disk, but can not format it (read only)
With F3b I can write to the drive, but only once (takes up the total disc), no multiple sessions. So where does F3b gets its drive definition from?
My question is, is this **read only** forced by the kernel, or is there a file that i can edit in order to make it **read/write** and usable by Brasero?
I prefer Brasero, because with the latest update it now allows easely multisession while I can stil not achieve it with K3b
Please give me some directions how I could overcome this "Read Only" limitation in a simple way, I am not very familiar with Linux procedures.
Tks in advance

---

### Post by Rogierdg on 2010-06-30
Because I had no reaction on my post, I try again.

I am unable to burn a CD-RW (new, erased, tried several brands) on the internal CD drive (/dev/sr0) of my laptop with either **CD/DVD Creator or Brasero** since I upgraded from Ubuntu 9.04 to 10.04.** Disk Utility** lists any inserted disk as **Read Only**. An USB attached external cd/dvd drive is recognised as rewritable and works fine. Since I use my laptop mostly on travel, it is not a solution to carry an external CD/DVD drive with me to save my data.

The stange fact is however that** F3b does** **recognise** the inserted disk on the internal cd drive as rewritable and can burn data to it provided it is erased or empty in the first place, but then it does not allow any further appends, the disk is flagged as full.

First I would like to know if this is a known bug, (I read somewhere that Udev may be at cause) and second how comes the same hardware is seen differently by CD/DVD Creator and F3b? Are there different places where the hardware capabilities are defined? Can these be changed?

Somebody in the community must have some idea about this.

Thanks in advance for any help, I would not like go backlevel to 9.04, or worse to MSWindows in order to make my system usable.

Rogierdg

---

