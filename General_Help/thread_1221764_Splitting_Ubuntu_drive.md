---
title: "Splitting Ubuntu drive"
date: 2009-07-24
forum: General Help
---

### Post by infiniah on 2009-07-24
I have Ubuntu on my 250gb drive, not dual booting with anything... and I haven't done this before ON UBUNTU; splitting the drive so i can put windows 7 on the other half or whatever space I choose to use... 
basically, how can i split my drive.

---

### Post by Mka on 2009-07-24
Use Gparted.
```
sudo apt-get install gparted
```
Resize your ubuntu partion using gparted. Leave as "unallocated space" enough size so that windows will fit and for your needs, say about 25GB. Install windows on that unallocated space. Windows will ask you to format it (i prefer when windows does the formating, not to say GParted cant format ntfs, or it cant?). 

You will need the ubuntu live CD after you windows is done installing in order to restore GRUB back to the MBR (other alternatives suck).

---

### Post by infiniah on 2009-07-24
hmm i have it installed but how do I resize. the option is in the list but not available to click. its resize/move, i don't know whats going on is this bad?

---

### Post by Cheesemill on 2009-07-24
You need to run gparted from the Live CD. You cant resize partitions while they are mounted.

---

### Post by infiniah on 2009-07-24
yeah i JUST figured that out :P 
thanks though

---

