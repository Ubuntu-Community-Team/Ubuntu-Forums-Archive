---
title: "Removing abandoned downloads"
date: 2009-12-24
forum: General Help
---

### Post by ram2500 on 2009-12-24
Hi there,

I was downloading Lotus Symphony to try out. Unfortunately, I was hoovering the room, and I accidentally bumped the power cords to my computer, cutting the power. Even though it's only less than 20MB into the 200 or so MBs of the download, I would like to know how to delete stopped downloads. (I have to re-download Symphony as it won't pick up where it left off, of course.) Any ideas?

---

### Post by 3rdalbum on 2009-12-24
> **ram2500 said:**
> Hi there,

I was downloading Lotus Symphony to try out. Unfortunately, I was hoovering the room, and I accidentally bumped the power cords to my computer, cutting the power. Even though it's only less than 20MB into the 200 or so MBs of the download, I would like to know how to delete stopped downloads. (I have to re-download Symphony as it won't pick up where it left off, of course.) Any ideas?

Why won't it delete in the file browser?

The other thing you could try is finding the URL of the Lotus Symphony file, and then feeding it into "wget" with the --continue option.

```
wget --continue http://www.foo.com/file.bin
```

---

### Post by x33a on 2009-12-24
which software were you using to download the files?

---

### Post by prshah on 2009-12-24
> **ram2500 said:**
> I would like to know how to delete stopped downloads.

If you were using Firefox, then usually incomplete download files will have a *.part filename. Eg, if you were downloading file1.exe, then the incomplete download filename will be file1.exe.part, and will exist in the same directory that would hold the completely downloaded file.

You can just delete the *.part file to prevent any resume (assuming resume is supported in the first place).

---

