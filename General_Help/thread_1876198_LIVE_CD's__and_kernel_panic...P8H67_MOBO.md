---
title: "LIVE CD's  and kernel panic...P8H67 MOBO"
date: 2011-11-05
forum: General Help
---

### Post by wannabegeek on 2011-11-05
Hi all

I'm still trying to get my new MOBO  Asus P8H67-m PRO with an i3 CPU, corsair 4GB DDR3 RAM
to play nice with Ubuntu.

I've realized that this MOBO doesn't appear to support IDE HD, which is fine since I am upgrading my 
OS drive anyways, but I also can't get any Live CD's to load.

I tried Ubuntu 11.10 and got a kernel panic, same goes for Parted Magic 6.7......

I ran a memtest86 and had no errors. My PSU is new. I still haven't gotten my SATA drive for the OS, 
but I thought I should at least be able to load a Live CD.

I have found one other thread about Ubuntu 10.10 not mounting as a Live CD....the author's
solution was to use a USB drive.

I am borrowing a USB optical drive and SATA HD on Monday, to start another round of testing.

I am hoping to get more ideas before with the forum's collective wisdom.....

I appreciate your help,
TIA,
wbg

---

### Post by dcstar on 2011-11-05
> **wannabegeek said:**
> Hi all

I'm still trying to get my new MOBO  Asus P8H67-m PRO with an i3 CPU, corsair 4GB DDR3 RAM
to play nice with Ubuntu.

I've realized that this MOBO doesn't appear to support IDE HD, which is fine since I am upgrading my 
OS drive anyways, but I also can't get any Live CD's to load.

I tried Ubuntu 11.10 and got a kernel panic, same goes for Parted Magic 6.7......

I ran a memtest86 and had no errors. My PSU is new. I still haven't gotten my SATA drive for the OS, 
but I thought I should at least be able to load a Live CD.

I have found one other thread about Ubuntu 10.10 not mounting as a Live CD....the author's
solution was to use a USB drive.

I am borrowing a USB optical drive and SATA HD on Monday, to start another round of testing.

I am hoping to get more ideas before with the forum's collective wisdom.....

I appreciate your help,
TIA,
wbg

One of the steps all Linux systems seem to do is probe for hard drives on the assumption that at least one will be found on the system.

If you do not have any hard drives on your system then all bets are off, I'd say.

---

### Post by wannabegeek on 2011-11-05
thanks dcstar...that's a good nugget of info....


I will now try to run a Live CD of Ubuntu 11.10 with a SATA drive connected.
This drive has all my movies and no OS...

I think I did try this before...

---

### Post by bluexrider on 2011-11-05
Recommend finishing the build then installing a OS.

---

### Post by wannabegeek on 2011-11-05
I thought that I did complete my build of this media server... until I couldn't install an OS.

Now I think that it may have to do with the HD not being a SATA drive...

I just tried using a USB version of Live 11.10 with my media drive connected which is SATA.

Have the error:
Kernel Panic - Not syncing VFS unable to mount root fs on unknown block.

UPDATE:

I changed the BIOS  settings for the SATA controller to disabled. Then tried my old IDE drive with Ubuntu 11.10 installed on it.
It started to boot and I got an interesting error:
"Bad Page Table"  

which is a similar error i got when trying my questionable Windows7 install disks...

---

### Post by wannabegeek on 2011-11-05
sorry to bump early ...but I am need to make some progress with this set up in case it needs to be returned...

anymore ideas about the kernel panic ?

---

### Post by dcstar on 2011-11-06
> **wannabegeek said:**
> I thought that I did complete my build of this media server... until I couldn't install an OS.

Now I think that it may have to do with the HD not being a SATA drive...

I just tried using a USB version of Live 11.10 with my media drive connected which is SATA.

Have the error:
Kernel Panic - Not syncing VFS unable to mount root fs on unknown block.

UPDATE:

I changed the BIOS  settings for the SATA controller to disabled. Then tried my old IDE drive with Ubuntu 11.10 installed on it.
It started to boot and I got an interesting error:
"Bad Page Table"  

which is a similar error i got when trying my questionable Windows7 install disks...

Boot up the CD and run the memtest option.

Also reset the BIOS to default settings.

---

### Post by wannabegeek on 2011-11-06
@dcstar....

Yeah I have run memtest86+ for a few hours and there's no reported errors in the memory.

However, I did look up on the Corsair site, that the RAM I have is not the exact same as the one on their list of compatible memory for the MOBO. 

I have CMX4GX3M1A11333C9  and the one from Corsair guaranteed-compatible list for a single chip is
CMV4GX3M1A1333C9

I am hoping that I can exchange the memory today from the dealer. I asked the dealer to choose this all for me since this is my first build. I didn't know about QVL lists and such things....

---

