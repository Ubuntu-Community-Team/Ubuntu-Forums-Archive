---
title: "Only search for similar case sensitive file names?"
date: 2010-01-22
forum: General Help
---

### Post by TormentedTeddy on 2010-01-22
Hello,

Anybody know of a way to search only for similar case sensitive files? By which I mean doing a wildcard search across a drive & the only results are like: Abc.txt abc.txt VID_001.avi Vid_001.AVI .. etc.

I've already tried searching the forums & google but the closest I've found is regarding files with increasing numbers (music_001.mp3, music_002.mp3, etc), which doesn't quite fit with my issue, as they would be seen as different files on a case insensitive OS.

Thanks very much for any help!

---

### Post by nothingspecial on 2010-01-22
If I understand you correctly you need find with the -iname option.

For example say you are searching your /media/data drive and you want to find abc.txt but you are uncertain of the case

```
find /media/data -iname abc.txt
```

would match abc.txt Abc.txt ABC.txt abc.TxT etc etc.

---

### Post by TormentedTeddy on 2010-01-23
> **nothingspecial said:**
> If I understand you correctly you need find with the -iname option.

For example say you are searching your /media/data drive and you want to find abc.txt but you are uncertain of the case

```
find /media/data -iname abc.txt
```

would match abc.txt Abc.txt ABC.txt abc.TxT etc etc.


The only problem with that (or using Ubuntu's "Search for files" program) is the user either needs to know the name of the files or do a wildcard search & have a list of *every* file within the searched directory. My problem is I have case sensitive files going as far as 5 directories deep on a drive & they're mixed in with thousands of files that I'd like excluded in the search results.


Example:
```

/Documents/
|
+-- /Books/
|     |
|     +-- Autopsy.txt
|     +-- AUTOPSY.txt
|     +-- autopsy.txt
|     +-- WHEEEEE.txt
|
+-------- /Misc/
|          |
|          +-- Abc.doc
|          +-- ABC.doc
|          +-- abc.doc
|          +-- file.doc

```

The kind of searching I'm looking for is one that'd show all similar case sensitive files without having to know their name, but would also exclude those files that don't have a similar match (like WHEEEE.txt & file.doc)

---

