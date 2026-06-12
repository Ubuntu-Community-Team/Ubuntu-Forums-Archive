---
title: "Issue with file order"
date: 2010-08-11
forum: General Help
---

### Post by TygerTung on 2010-08-11
I have this audiobook to listen to on my MP3 player, but no matter how I rename the files, they won't come up in consecutive order. When you observe them in a window in ubuntu the order is fine, but when you observe them in my MP3 player the order is out of wack. I downloaded a peice of software 'pyRenamer' to rename the files to make them work, and they are in the same incorrect order on there too.

I havn't had this problem before with the previous 9 audiobooks I have put on my MP3 player.

Any help would be great!!!!

---

### Post by mprokolo on 2010-08-11
if i remember correctly nautilus has different order than for example the terminal (ls command) Simple fix is that you should put a zero before every number if you have more than than 10 files (ex 01 02 etc.)

post the ```
ls
``` output if you want more help

---

### Post by TygerTung on 2010-08-11
It came out with the files in this order.

```
010.mp3  013.mp3  016.mp3  019.mp3  021.mp3  02.mp3  05.mp3  08.mp3
011.mp3  014.mp3  017.mp3  01.mp3   022.mp3  03.mp3  06.mp3  09.mp3
012.mp3  015.mp3  018.mp3  020.mp3  023.mp3  04.mp3  07.mp3
```

I put a zero in front though, I don't know what is causing this problem.

---

### Post by SlugSlug on 2010-08-11
find a MP3 tag renamer - my bet is that file browser reads filenames -- music player thingy reads mp3 tags

unless looking at that ^^  does it play in the order of 

ls -l ?

---

### Post by TygerTung on 2010-08-11
it did before, but with the zero's in front of it is worse, with it going in order of 01, 010, 011, 012 etc then 02, 020, 021, 022, 023, 03, 04, 05, 06, 07 etc.

---

### Post by TygerTung on 2010-08-11
I deleted the ID tags and that didn't help.

---

### Post by Ron Ruble on 2010-08-11
The file order you observe is correct.

The problem is that you should have added zeros before the file names **only** where needed to make all file names the same number of character positions.

The sort order is character (alphabetic), not numeric.

Rename all 2 character file names by adding a zero in front of them, so that all file names are 3 characters, plus extension.

A little more explanation:

010.mp3 sorts before 01.mp3 because the second 0 in 010.mp3 sorts before the dot in 01.mp3. All numbers sort before the dot.

Also, you mentioned using an MP3 player. The MP3 player is likely to be using VFAT. If so, you may need to move the files off the MP3 player, rename them, and then move them back to the MP3 player.

FAT file systems don't have a sort order. Files order in the data-time order the directory entry was created.

---

### Post by Vaphell on 2010-08-11
make all names consistent with a fixed number of digits , don't treat the file names as numbers but as an abstract string of characters. In case of 2digits 01,10,22, in case of 3 - 001,010,022

01.mp3 vs 011.mp3 vs 02.mp3
second char is 1 or 2, 2 is put after 1s
then to determine order among the 01x it compares 3rd chars (. and 1) - as you can see comparing dots with digits is not what you meant.

---

### Post by SlugSlug on 2010-08-11
rename to a.mp3 b.mp3 etc...?

---

### Post by TygerTung on 2010-08-11
Whoopie!!! That sorted her out! Thanks heaps!!!!

---

