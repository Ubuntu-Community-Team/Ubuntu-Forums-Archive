---
title: "How to format DVD-RAM to UDF?"
date: 2010-09-03
forum: General Help
---

### Post by AndrejaKo on 2010-09-03
Hi! 

Today I've found my cache of old DVD-RAM disks. I bought a couple few years back when I was experimenting with backup solutions using them. Anyway, to cut the long story short, they came formatted as FAT32. I tried to format the to UDF from windows, but format failed and I was unable to format them to UDF or FAT32, so I thought that there is some incompatibility between my drive and them or that I damaged them.

Today I decided to give them one more try before trashing them. I managed to format them to ext2 without any problems, but I'd like to use them on windows computers too.

I installed udftools and dvd+rw tools and tried to use 
sudo mkudffs --media-type=dvdram /dev/sr0

to format disks. Unfortunately, the response was: 
"trying to change type of multiple extents"


What does that mean and how can I fix that?

EDIT:
On another forum, I was advised to try with dvd+rw-format /dev/dvd -format=full -ssa=default

he format did complete, but I still get the same error from mkudffs and I still have no idea what to do.

---

