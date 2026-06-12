---
title: "Finding similar file names"
date: 2012-09-12
forum: General Help
---

### Post by johnsnails on 2012-09-12
Hi,

Looking for some suggestions...

I have a folder with a few hundred files, some are duplicates but with slightly different names, so for example.

file1.txt and file1(2005).txt

I was looking for a program that can scan a folder and report the files it deems to be similar so I can check them and delete them if need be.

Thanks in advance.

---

### Post by Statia on 2012-09-12
I have done something like that recently, however, the program I used does not look at filenames, but uses a file fingerprint (I believe a MD5 hash) to check if the files are identical. That means that even the filenames are completely different, it also finds duplicates.It is called fdupes.

---

### Post by johnsnails on 2012-09-12
> **Statia said:**
> I have done something like that recently, however, the program I used does not look at filenames, but uses a file fingerprint (I believe a MD5 hash) to check if the files are identical. That means that even the filenames are completely different, it also finds duplicates.It is called fdupes.

I did come across fdupes, i was thinking it would work, but some of these files could actually be different md5's because of the different torrent sites *cough* they might have come from :P

---

### Post by johnsnails on 2012-09-12
I think I will mark this as solved, because I underestimated how fdupes worked and it will still help enormously.

Thanks!

---

