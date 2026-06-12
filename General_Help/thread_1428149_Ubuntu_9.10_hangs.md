---
title: "Ubuntu 9.10 hangs"
date: 2010-03-12
forum: General Help
---

### Post by sat4ever0606 on 2010-03-12
i don kno wats the prob with the karmic koala! i recently installed ubuntu on my machine, it installs perfectly but after it goes in it hangs like hell either when ubuntu loads or after the user interface comes !!! i thought the prob was w/o swap and then i allocated 5gb for root in ext4 filesystem and 2 gb for interface and it froze!! I then tried changing to the following configuration

5gb ext3 --->/
1gb ext3 --->/home
1gb ---------> swap area

stil it hangs terribly!!! i tried formatting and installing again more than 6 times stil no luck :(

---

### Post by cottfcfan on 2010-03-12
Where is it hanging exactly and for how long. Sometimes its a BIOS problem. 
 Plus 1GB Home folder is extremely small, how much space do you have to play with?

---

### Post by sat4ever0606 on 2010-03-13
actually it hangs almost anywhere! sometimes when ubuntu keeps loading it hangs! or some other time it hangs after the gui has come up and i click something it hangs!!
i have a 512mb ram 160gb hd intel core 2 duo processor!!

i allocated as follows

5gb-->/ (ext3)
1gb-->/home(ext3)
1gb-->swap

---

### Post by cottfcfan on 2010-03-14
I`m no expert but your partitioning looks ify.
You`ve got 160 gb Hard Drive. But you only allocating 7Gig to Ubuntu, and only 1 Gig to the Home Folder. Maybe its hanging because its struggling to mount a partition.

---

### Post by cottfcfan on 2010-03-14
I`m no expert but your partitioning looks ify.
You`ve got 160 gb Hard Drive. But you only allocating 7Gig to Ubuntu, and only 1 Gig to the Home Folder. Maybe its hanging because its struggling to mount a partition.
 If your going to allocate such a small amount to linux I wouldn`t
partition it like that.
 I`d reinstall and just use the whole 7 Gig as one partition "/"

---

### Post by sat4ever0606 on 2010-03-17
did installing 7 gb and installed inside windows and yet it hangs!!! :mad: :mad: :mad: :mad:

---

### Post by cottfcfan on 2010-03-17
You`ll have to give all your hardware specs.
Sometimes it happens that certain computers running certain hardware just don`t like Linux.

---

### Post by sat4ever0606 on 2010-03-17
i've intel core2duo e4400 processor
160 gb hard disk
512mb ram
've installed x86 ubuntu!

---

### Post by cottfcfan on 2010-03-17
Sorry should have read your above post.
If youve now installed x86 Ubuntu, what were you trying to install before?

---

### Post by sat4ever0606 on 2010-03-17
first installed 32 bit ubuntu some ten times.. then thought maybe 64bit wud solve the prob and instal'd't(separate partition)!!! but tat 2 hangs like 32 bit!!! now removed 64 bit and tried installing 32bit ubuntu using wubi and allocated 7 gb and installed!!! installations were fine like usual but stil it hangs!!! now i've not allocated any swap or and the like!!

---

### Post by nitstorm on 2010-03-17
Maybe boot in using a different kernel ????

---

### Post by cottfcfan on 2010-03-17
I wouldn`t use 64bit if tou have only got 512mb memory.
 Instead of using Wubi why don`t you just partition your hard drive, and dual boot with windows?

---

### Post by sat4ever0606 on 2010-03-17
in dual boot ubuntu hang'd! so i thought of installing inside windows!also wen i immediately saw the memory usage in ubuntu(did it v fast b4 it could hang) i saw that oly 130mb ram was been used (32 bit) and wen i tried to close it as usual it hang'd! :X

---

