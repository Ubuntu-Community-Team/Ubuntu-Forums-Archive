---
title: "Eliminating double files"
date: 2010-02-04
forum: General Help
---

### Post by GabrielWolff on 2010-02-04
I had a HDD crash the other day.
- I managed to recover some of my files, but many of them without names. 
- I have partial backups of different folders.

Is there a script/program that makes it possible to find all those files that exist in both the backup and the recovered partition?
I would need something that can ignore name/date (as those got erased) and really compares the files in depth.

---

### Post by chewearn on 2010-02-05
I'm not sure about an application that could do what you wanted.

If I have to do this manually, I would:
1. dump the entire list of files into a text file or a spreadsheet
2. sort by file size
3. remove everything except files with same sizes
4. calculate md5sum of remaining files
5. sort by the md5sum

Therefore, files with same md5sum should be identical.

---

### Post by GabrielWolff on 2010-02-05
> **chewearn said:**
> I'm not sure about an application that could do what you wanted.

If I have to do this manually, I would:
1. dump the entire list of files into a text file or a spreadsheet
2. sort by file size
3. remove everything except files with same sizes
4. calculate md5sum of remaining files
5. sort by the md5sum

Therefore, files with same md5sum should be identical.

No way! Are you serious? Around 1000 of these files are .sib and .mus files, thus having exactly the same size. There must be some program/script to check these things automatically, no?

---

### Post by StuartN on 2010-02-05
> **GabrielWolff said:**
> No way! Are you serious? Around 1000 of these files are .sib and .mus files, thus having exactly the same size. There must be some program/script to check these things automatically, no?

```
fdupes -R .
```

This will list every pair (or group) of files that having matching md5 checksums, whatever the filename. It is also really quick. (You will need to install fdupes, which is in the repositories).

As an alternative, install Krusader and use the "Synchronise directories" tool. This generates a list of differences (or matches), assuming files have the same name and location.

---

