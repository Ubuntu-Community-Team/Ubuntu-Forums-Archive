---
title: "Bug in File Browser, Ubuntu 10.04"
date: 2010-10-03
forum: General Help
---

### Post by Cokaric on 2010-10-03
I connected my USB drive and downloaded on it allot of songs. Now I wanted to edit the song tiles from >>

```
opca opasnost - treba mi ne&#353;to jace od sna.mp3
```to
```
Opca Opasnost - Treba mi ne&#353;to jace od sna.mp3
```Tryed on this file also >>

```
HAMMERFALL - Any Means Necessary.mp3
```to
```
Hammerfall - Any Means Necessary.mp3
```But then this Error pops up >>

[IMG]http://i56.tinypic.com/11vnyw5.png[/IMG]

AND

[IMG]http://i52.tinypic.com/16m999e.png[/IMG]

Error only happens when I'm trying to rename files on USB drive. Tested in root and on Desktop and it worked without any problems.

Sorry that I am reporting but here but I don't have time to read all of the instrucions there how to report a bug. I suggest some make a easy way to report bugs in Ubuntu cause that way is too long and complicated for some little bugs like this... Especially cause its wasting my time that I don't have that much.

p.s.
Maybe bug or its meant to work like that but when you past file named "FILE.mp3" to a folder (on the HDD not USB drive) that already contains file named "file.mp3" it copies it to a folder without any problems, so I assume he's comparing ASCII value of each letter in name, and since they are different it writes the same file. Would be interesting to see how does the function for copying files in Ubuntu look like but as I said I don't have time to waste...

All the best,
Cokaric

---

### Post by oldos2er on 2010-10-03
What file system is on the USB drive?

---

### Post by The Cog on 2010-10-03
I guess you are using a FAT filesystem. The driver won't let you rename filename to Filename because the only difference is upper/lower case. FAT doesn't distinguish between upper and lower case filenames.

Once you copy the files to a filesystem that does distinguish between the two, the problem will go away.

---

