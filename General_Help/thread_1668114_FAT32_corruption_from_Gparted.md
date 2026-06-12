---
title: "FAT32 corruption from Gparted"
date: 2011-01-15
forum: General Help
---

### Post by macoklein on 2011-01-15
Hello everyone, 
I have a Lenovo T400 dual booting ubuntu 10.10 and windows 7. Since I often have to use both operating systems, I set up a FAT32 partition about 2 years ago so that I could store music, photos, school documents etc, and have windows be able to access them. However, yesterday I did something stupid.

I was enlarging the partition, using Gparted, and, without thinking, I stopped the process about half way through. Naturally this corrupted the FAT. 

I am familiar with using dd and photorec, so I have a binary of the partition and all of the files back (but their names and folder structure is destroyed). I also have a back-up that is fairly recent so it is not horrible if I simply reformat the partition and copy the backup into it. however, I am curios, since Gparted was only moving the FAT left (down in sector number), is there any simple way to repair the FAT and get my directory structure and file names back? 

Thanks!

---

