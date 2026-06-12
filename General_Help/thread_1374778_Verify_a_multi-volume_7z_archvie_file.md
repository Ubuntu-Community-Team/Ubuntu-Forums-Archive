---
title: "Verify a multi-volume 7z archvie file"
date: 2010-01-07
forum: General Help
---

### Post by ario on 2010-01-07
Hi.
I used 7z to create a multi-volume 7z archive file with 0 compression rate. with this command:
```
7z a -t7z -v1g -mx0 /home/movies/documents.7z /home/documents
```
**a**      stands for add
**t**      stands for type definition
**7z **    stands for 7z archive type
**v1g**    stands for creation of maximum 1GB volumes
and **mx0** stands for zero compression rate. because I just need to store a file system to an archive file very fast and without any compression to then burn it in many DVDs.

Now I do not now **how to verify created archive files.** It gave me these files:
```
documents.7z.001
documents.7z.002
documents.7z.003
documents.7z.004
documents.7z.005
documents.7z.006
documents.7z.007
documents.7z.008
```

I used tar but it can't handle 7z archives.
Any Idea?
Thanks for your attention guys.:)

---

### Post by SlugSlug on 2010-01-07
extract it and see if it works?

---

### Post by michy99 on 2010-01-07
I am not aware of any way to do it without extracting the files and checking the crc for each file. I hope you know that 7z does not store owner/group information.

---

### Post by ario on 2010-01-07
I can not extract and change all files. because archive contains more than thousands of files in it! This is why I want to archive files without any compression and then place them in DVDs. because DVD ISO file format can support a limited amount of filename and path lentgh.
Any Suggestions?

---

