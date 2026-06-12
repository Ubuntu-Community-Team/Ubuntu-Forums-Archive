---
title: "Memory card currupted need  help ???"
date: 2009-07-02
forum: General Help
---

### Post by rushikesh988 on 2009-07-02
hello friends,

My memory card get currupted during recieving the files from other mobile ..
now neither my mobile is mounting it nor my UBUNTU ....is there is any tool or command by which I cammand for repairing  it ...



I tried force mount but no effect

---

### Post by scrooge_74 on 2009-07-02
conect the phone back to your PC with the card inside.

Open a terminal and type dmesg

The last few lines should tell you under what name the system is recognizing the card,

Then type sudo fdisk /dev/sdb1 (change the sdb1 to yours)

finally 

sudo mkfs -t vfat /dev/sdb1

This will reformat it and you will lose everything on it but will let you use it again.

---

