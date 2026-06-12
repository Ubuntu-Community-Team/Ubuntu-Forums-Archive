---
title: "how to bunzip2 a sparse file"
date: 2010-12-08
forum: General Help
---

### Post by nw221 on 2010-12-08
I have a bzip2 compressed disk image, and I would like to uncompress it again onto my disk without using up lots of space, in fact there isnt enough space on my disk if I were to uncompress it as is. However it was a sparse file with lots of space in its original form, so I know it will fit if I can uncompress it directly as sparse. Is there some combination of bzip2,cat,cp,dd or friends I can use to pipe the output from bzip2 directly to a sparse file again?

Thanks a lot for your suggestions!

---

### Post by nuno.sucena on 2011-02-27
Hi, you can use tar --sparse (or -S)

-S , --sparse 
 handle sparse files efficiently

create file:
tar cvSfj file.tar.bz2 sparsefile

and then uncompress:
tar xSf file.tar.bz2

---

