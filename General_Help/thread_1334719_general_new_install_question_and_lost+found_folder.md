---
title: "general new install question and lost+found folder question)"
date: 2009-11-22
forum: General Help
---

### Post by expxe on 2009-11-22
i currently have windows 7 and ubuntu 64 bit dual booting on one hard drive. i plan to get a ssd later and install ubuntu on that and it will be my main drive then. will i have any problems accessing all the files on the dual boot drive from my ssd drive? or will the folders be locked to the original user? i plan to wipe the drive but after i move the important files into a separate partition first (and then merge them later) so i don't have to burn around a whole bunch of back up dvds. i just want to make sure i can even access the files on there before the move

a new question here, i recently formated a partition used to have an old install of ubuntu on it but after the format there is a folder called lost+found that takes up around 13 gb and i can't seem to delete it, any help on that?

expxe

---

### Post by dcstar on 2009-11-22
> **expxe said:**
> i currently have windows 7 and ubuntu 64 bit dual booting on one hard drive. i plan to get a ssd later and install ubuntu on that and it will be my main drive then. will i have any problems accessing all the files on the dual boot drive from my ssd drive? or will the folders be locked to the original user? i plan to wipe the drive but after i move the important files into a separate partition first (and then merge them later) so i don't have to burn around a whole bunch of back up dvds. i just want to make sure i can even access the files on there before the move

a new question here, i recently formated a partition used to have an old install of ubuntu on it but after the format there is a folder called lost+found that takes up around 5 gb and i can't seem to delete it, any help on that?

expxe

An Ubuntu install always creates the first user with an UID of 1000, so you can be fairly confident that with your new install you can access the files created with same UID on the old install.

Search for instructions on a separate /home partition, that will solve your problem.

EXTn partitions always have reserved space for system use, do not touch these.

---

### Post by expxe on 2009-11-23
but why would there be a folder called lost+found?

---

### Post by fluffman86 on 2009-11-23
lost+found is a system folder where things go that appear to be broken.  Like if you system doesn't shut down properly, and your computer runs a fsck on bootup, and it finds something funky looking, it goes in lost+found.

---

### Post by expxe on 2009-11-24
[quote=dcstar;8368818]An Ubuntu install always creates the first user with an UID of 1000, so you can be fairly confident that with your new install you can access the files created with same UID on the old install.

Search for instructions on a separate /home partition, that will solve your problem.
[B]
EXTn partitions always have reserved space for system use, do not touch these.[[/B]/quote]

but is having a lost+fond folder normal?

and i lost 13 gb of space (out of 98gb), is that normal?

---

### Post by lisati on 2009-11-24
> **expxe said:**
> [quote=dcstar;8368818]An Ubuntu install always creates the first user with an UID of 1000, so you can be fairly confident that with your new install you can access the files created with same UID on the old install.

Search for instructions on a separate /home partition, that will solve your problem.
[B]
EXTn partitions always have reserved space for system use, do not touch these.[/B]

but is having a lost+fond folder normal?

and i lost 13 gb of space (out of 98gb), is that normal?[/QUOTE]I've had "lost and found" myself one or two times, and have managed to free up a bit of space by carefully looking at what was in the folder. It won't hurt to be a bit choosy about what you delete.

---

### Post by expxe on 2009-11-24
ubuntu is telling me i don't have permission to view the inside of the folder. the partition used to hold a botched up ubuntu install

---

### Post by expxe on 2009-11-26
bump it up baby

---

