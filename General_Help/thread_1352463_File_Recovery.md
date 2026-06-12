---
title: "File Recovery"
date: 2009-12-11
forum: General Help
---

### Post by keenansnews on 2009-12-11
Accidently, I reformatted my SD memory card for my Casio camera.  I've tried several Linux programs to recover these jpg and hd video files: magicrescue, foremost, photorec, recoverjpeg and scalpel.  I am unable to recover jpg (or hd video) from my reformatted SD memory card.

I decided to do a little testing of these programs ability to recover files on another SD memory card.  They successfully recovered jpg files that were deleted, but would not recover jpg on a memory card that had been reformated.

 I thought reformating  would only clear references to files, not disturb file data.

 Anyone know what is going on or know of a tool that will find these files?

---

### Post by aysiu on 2009-12-13
In theory reformatting should still allow you to recover deleted files, but it appears in this case those particular files are unrecoverable. Sorry.

---

### Post by keenansnews on 2009-12-14
> **aysiu said:**
> In theory reformatting should still allow you to recover deleted files, but it appears in this case those particular files are unrecoverable. Sorry.

Do you have some inside information why you would so it's unrecoverable?

I doubt the formatter went through a erased the magic numbers.  I'm thinking I may have to break out some python code and seek the volume for magic ending and beginning numbers.  I may have to do a little research on vfat in case of fragmented files.  But, that should be  a basic jump to location flag, so it should not be too much of a problem.

I hate to have to reinvent the wheel, but if the basic linuxe tools are not working when they should, there is no other choice.

---

