---
title: "Advantages of tar archive"
date: 2011-08-13
forum: General Help
---

### Post by r.darwish on 2011-08-13
The tar archive format seems like the most popular format in the Unix world. While all major Linux distributions supports newer formats, it seems most users still stick with the old tar format which supports less features than others.
This keeps me wondering: Is there any specific reason(s) that while most Linux distributions offers new archive formats, the old tar format is still popular? Does it have any advantages over newer formats like 7zip or zip?

---

### Post by haqking on 2011-08-13
> **r.darwish said:**
> The tar archive format seems like the most popular format in the Unix world. While all major Linux distributions supports newer formats, it seems most users still stick with the old tar format which supports less features than others.
This keeps me wondering: Is there any specific reason(s) that while most Linux distributions offers new archive formats, the old tar format is still popular? Does it have any advantages over newer formats like 7zip or zip?

7zip and tar are not compression formats, .tar  is a packaging format/file format, the compression would be the .gz etc part added to it such as .tar.gz

7zip is an application with an output of many inlcuding .tar.

and if you download the linux source for 7zip it comes down in a .tar.bz2 ;-)

---

### Post by r.darwish on 2011-08-13
I used incorrect terms. I know that 7zip is a program which can handle multiple type of archive files. By saying "7zip" I meant the 7z archive format. 7z and Zip are archive formats that supports compression by themselves. Tar does not, and it relies on other programs to compress the whole archive. If I understand correctly, this can be a disadvantage when someone wants to extract a single file from a compressed tar archive, because the computer needs to actually decompress the whole archive in order to extract a single file.

---

### Post by haqking on 2011-08-13
> **r.darwish said:**
> I used incorrect terms. I know that 7zip is a program which can handle multiple type of archive files. By saying "7zip" I meant the 7z archive format. 7z and Zip are archive formats that supports compression by themselves. Tar does not, and it relies on other programs to compress the whole archive. If I understand correctly, this can be a disadvantage when someone wants to extract a single file from a compressed tar archive, because the computer needs to actually decompress the whole archive in order to extract a single file.


you can see a comparison here

[http://en.wikipedia.org/wiki/Comparison_of_file_archivers](http://en.wikipedia.org/wiki/Comparison_of_file_archivers)

then choose the most sutiable for your needs, though tar is a little dated it is tried and tested and works.

---

### Post by Dave_L on 2011-08-13
Reliability and downward compatibility are extremely important in an archive format.  If I had a five-year-old (or 10- or 15-year-old) archive I wanted to access, I would hate to find that I couldn't open it because the format is no longer supported or is incompatible with the current archiver.

That's why I'm content to stick with .tar.gz for most situations.

---

### Post by AlphaLexman on 2011-08-13
And, as storage space (hard drives, usb sticks) get bigger and cheaper, minimal compression ratio differences become less significant.

---

