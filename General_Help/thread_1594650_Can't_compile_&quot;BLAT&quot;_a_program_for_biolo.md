---
title: "Can't compile &quot;BLAT&quot; a program for biological sequence alignment"
date: 2010-10-12
forum: General Help
---

### Post by zslastman on 2010-10-12
Trying to get an important piece of alignment software to work on my 10.04 system, available only as a tarball. The readme states that I need to make sure that the variable $MACHTYPE exists on my system (it does - "i486-pc-linux-gnu"), make a directory ~/bin/$MACHTYPE (done) ensure that it's in my PATH (i exported it to my path) and then sudo make. I did all this and I get 



gcc -O  -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -DMACHTYPE_ -DJK_WARN -Wall -Werror -I../inc -I../../inc -I../../../inc -I../../../../inc -I../../../../../inc  -o common.o -c common.c
cc1: warnings being treated as errors
common.c: In function ‘firstWordInFile’:
common.c:1695: error: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
make[1]: *** [common.o] Error 1
make[1]: Leaving directory `/home/zlastman/src/blatSrc/lib'
make: *** [all] Error 2




Any ideas? The readme thinks my machtype variable should be of the form "i486" so i tried using that to create the directory and putting that in my path, again, no dice. The program isn't in the repositories. Thanks guys.
Heres my Path variable 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/zlastman/bin/i486/:

---

