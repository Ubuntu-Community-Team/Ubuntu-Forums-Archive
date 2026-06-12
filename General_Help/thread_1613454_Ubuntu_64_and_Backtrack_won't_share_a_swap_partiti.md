---
title: "Ubuntu 64 and Backtrack won't share a swap partition."
date: 2010-11-04
forum: General Help
---

### Post by winskitech711 on 2010-11-04
I'm triple booting Windows 7 32-bit (that's the only version I had), Ubuntu 10.10 64-bit, and Backtrack 4 R1.

Windows 7 installed and runs fine. Ubuntu installed and runs fine. I try to install Backtrack 4 R1, create a / partition, create a /boot partition (do I need to create a /boot for Backtrack?), and I don't create a swap file because the Ubuntu swap file is already in there.

I click "forward", the install starts up, then I get "The attempt to mount a file system with type swap...yadda yadda yadda...has failed." I google this, I get some results talking about an mkswap command, but in my noobness, I don't understand.

Can Ubuntu 64 bit and Backtrack not share a swap file? I don't want to create 2 swap files because I've googled around and that looks like a bad thing to do.

Help!

Thanks in advance,

Adam

---

### Post by 3Miro on 2010-11-04
I have shared swap between Ubuntu and Arch, Gentoo, Fedora and Lunar. No issues. What is the yada yada message, those are usually important.

---

### Post by winskitech711 on 2010-11-04
The yadda part is the location: SCSI3 (0,0,0), partition #5 (sda) at none.
 
After more research I'm beginning to suspect I need to install Backtrack first THEN Ubuntu.
 
I installed it: Windows 7, Ubuntu, then Backtrack.

---

### Post by 3Miro on 2010-11-04
Have you tried the Backtrack forum. They may know about this, I have never used it and I am surprised that it doesn't work since all other distros that I have tried do share swap with Ubuntu and they were not even based on Ubuntu.

---

### Post by winskitech711 on 2010-11-05
After more reseach I'm thinking my two options are 1) create a seperate boot partition for Backtrack 2) Wipe ubuntu off my system, install backtrack, then install ubuntu.
 
I tried option 1) creating a seperate boot partition for backtrack. Backtrack still wants to format ubuntu boot partition so I get the "The attempt to mount a file system with type swap SCSI3 (0,0,0), partition #5 (sda) at none has failed." error again. I'm not running the operating systems at the same time so nothing should be using the ubuntu swap partition.
 
Does backtrack just need to be installed first?
 
Thanks again in advance,
Adam

---

### Post by winskitech711 on 2010-11-05
Update!
 
I tried option 2 which was blowing all of the partitions out except for windows and letting back track create the partitions I needed including the swap partition.
 
1. I blew all of the partitions via gparted on a live Ubuntu CD.
2. Booted from a BackTrack 4 R1 disk
3. Ran through the installation process, set up my partitions, set up my swap partition
4. Start the install
5. Get this error: "The ext3 file system creation in partition #5 of SCSI3 (0,0,0) (sda) failed."
 
What am I doing wrong?

---

