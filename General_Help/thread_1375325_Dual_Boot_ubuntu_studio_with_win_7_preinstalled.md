---
title: "Dual Boot ubuntu studio with win 7 preinstalled"
date: 2010-01-07
forum: General Help
---

### Post by hasizo on 2010-01-07
Dear users.

I've been having serious problems installing the ubuntu studio 9.10 - and I've spent at least 8 working hours trying to figure things out on the internet.

Here is what I've done: (PLEASE NOTE, I'm running a QUAD-CORE **64 BIT** (AMD))

1) Bought an EMPTY computer

2) Installed ubuntu studio 9.10 **64 bit** (while waiting for win 7)

3) LOVED the ubuntu, but deleted everything and installed win 7 Ultimate **64 bit**

4) started missing ubuntu studio with it's perfect awesomeness (it's free, and very high quality)

5) Started wondering about ways to dual boot (note: never heard about the term until then)

Here is what i tried:

1) finding step-by-step manuals on the internet (failed)

2) virtual box (didn't like the idea that it was a boot-inside-a-boot)

3) Wubi (worked great, until i realized that it wouldn't let me upgrade to ubuntu studio)

4) panicking

5) spending hours searching on the internet, partitioning my HD like this:
- 1 drive only for win 7
- 1 drive only for win 7 swap-file
- 1 drive for ubuntu
- 1 drive for win-docs and programs
- 1 drive for... "stuff"

note: "drive" = "partition"

6) deleting the ubuntu drive/partition leaving 20Gb of unallocated space

7) testing if ubuntu studio would recognize the unallocated space and take care of the rest.

8) looking at my ubuntu live cd and my ubuntu studio (not live) cd, thinking about using them as frees-bees

9) signing in here, hoping to find the answer I'm looking for.



Call me ignorant, call me noob-tard, just do it while you explain to me how i install ubuntu studio with out messing up my win 7 installation.

ps: I already know about the other post with something like "installing win 7 with ubuntu preinstalled", but that's NOT what I'm looking for.

Besides, this might help "NoUbunties" like me not getting scared of using ubuntu.

Pleeease, anyone?.... free online-popcorn for everyone!

:popcorn:

---

### Post by audiomick on 2010-01-07
> 7) testing if ubuntu studio would recognize the unallocated space and take care of the rest.

So what happened exactly when you tried to run the Ubuntu Studio installer?

---

### Post by Paul Stone on 2010-01-07
I have been unable to install Ubuntu 9.10 on top of Windows XP.  Every time I try, I get an unbootable system (I chalk it up to the transition to Grub2).  If that happens to you, use your Windows CD to fix the system, so that Windows 7 is able to boot again.

If you google "Windows-7 FIXMBR FIXBOOT", you'll find all kinds of instructions.

Basically, you should be able to install Ubuntu onto a Windows system and boot both of them.  Ubuntu can resize your Windows partition or make use of the unused space on the drive.  But, my experience is that it doesn't work, and I get an unbootable system.

It still may be worth a try, since it's not that difficult to recover the capability to boot Windows.  Seems like the dual-boot install is working for a lot of other people.

Anyway, it's pretty simple.  Just install and follow the instructions.  There is an option during partitioning to allow you to choose at boot time which operating system to start.

Good luck!

---

### Post by Leppie on 2010-01-07
- Get the Ubuntu studio iso: [http://cdimage.ubuntu.com/ubuntustudio/releases/9.10/release/ubuntustudio-9.10-alternate-amd64.iso](http://cdimage.ubuntu.com/ubuntustudio/releases/9.10/release/ubuntustudio-9.10-alternate-amd64.iso)
- Get the checksums file: [http://cdimage.ubuntu.com/ubuntustudio/releases/9.10/release/MD5SUMS](http://cdimage.ubuntu.com/ubuntustudio/releases/9.10/release/MD5SUMS)
- Open a terminal and go to the folder where you put the iso and md5 cheksum file and check the checksum of the iso:
```
md5sum -c MD5SUMS
```
- Burn the iso (best at speeds inferior to 10x)
- Boot with the freshly burned Ubuntu Studio dvd
- Install Ubuntu Studio, installation guide: [https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install](https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install)
- Enjoy Ubuntu Studio ;)

---

### Post by hasizo on 2010-02-07
Hi again people.

Things have been kinda hectic (med school exams).

I succeeded with the following strategy:
1) install win 7
2) partition the harddrive, and LEAVE A GOOD PORTION OF UNALLOCATED SPACE (my HD is about 600GB, I left 100GB for ubuntu studio)
(I used the "magic partitioner"... it's free and works 100%)
3) install ubuntu studio, and select "use largest free space available" (or whatever it's called)

THAT'S IT... 3 easy steps.

Thx Y'all!:popcorn::KS

---

