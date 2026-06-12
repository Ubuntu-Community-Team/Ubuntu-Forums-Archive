---
title: "Segmentation fault"
date: 2010-01-27
forum: General Help
---

### Post by newport_j on 2010-01-27
**[B]Segmentation fault** [/B]
**The following code works when compiled to 32-bit program and run on a 32-bit Ubunut 8.04. **
 
 
**#include <stdio.h>**
 
**int main(int argc, char *argv[]){**
 
**int i, j, k;**
**double Rdiff;**
**double Temp;**
**FILE *fid; **
**/* Initialize Sorce and Reciver locations */**
**fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");**
**fscanf(fid,"%*[^\n]");**
**fscanf(fid,"%*[^\n]");**
**fclose(fid);**
**};**
 
 
**When it is compiled as a 64 bit program and run on a 64 bit Ubuntu it gives a segmentation fault. The error line or the crash line is:**
 
**fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");**
 
 
**Now when I compile it to a 32 bit program and run it on a 64 bit Ubuntu it also crashes. **
 
**I am not sure why it does. It seems to have something to do with fid.**
 
**This was originally on the Absolute Beginner Ubuntu Forum, it was suggested I move it to the Developer Forum, but the Developer Forum is not takng new posts. I am putting the question here. It is an alternative to the Developer Forum; which I could not post into.**
 
 
 
**[B][COLOR=#ff0000]Newport_j[/COLOR]**[/B]
**[B][COLOR=#ff0000][IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG][/COLOR]** [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8733541") [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG][/B]
**[COLOR=#ff0000][IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG][/COLOR]** [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8733541") [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by rnerwein on 2010-01-27
hi
your problen is: **fid = fopen("../TestJigs/Inputs/LIB/Acoustics/SorRec.in","r");**[B]
failed. ask for the return code. i guess it's NULL. you can use ltrace to see whats really hapens.
the segmentation fault comes from fscan(fid,....) because fid is a NULL-Pointer.
--> ltrace ./your_program
__isoc99_fscanf(0, 0x4007b3, 0x4007b3, 4096, 0x7f4
                          ^
ciao
[/B]

---

