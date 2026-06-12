---
title: "tar backup help?"
date: 2009-08-26
forum: General Help
---

### Post by DejitaruJin on 2009-08-26
Okay, I have RAID working (I hope), and I intend to use it. Unfortunately, it seems I need some help with the tar command. I mean, I'm just trying to do what half the servers in the world must be doing, but the tar command doesn't make it easy, and it seems there's little information on the subject.

First and foremost, these are Windows files. Spaces and lengthy filenames abound. This is where the main complications come from. To cover this, I would normally tell it to backup something along the lines of "*", or "/mnt/250GB/tests/*". But it gets very confused by the wildcard.

I've tried passing the data through ls and find, but the result still isn't something tar can readily use. Adding something like `find "/mnt/250GB/tests/*"` *still* interprets the * literally. Moving the quotes outside of the ` for some reason interperets the whole output as a single line. Without the quotes, the spaces cause the same problem as originally.

How in the heck do I make this work?

---

### Post by danwood76 on 2009-08-26
If you want to tar an entire directory you simply use the dir path so "/mnt/250GB/tests" the * will tar all files in that directory but not sub directories.

What exactly are you trying to do?
You should easily be able to tar windows files.

If you are looking for a server style backup you might want to use rsync or one of its derivatives as it will save you on server load.

---

### Post by psycho on 2009-08-26
Hi DejitaruJin.

I may be misunderstanding your question, but if you're asking how to use tar to archive everything under /mnt/250GB/tests/ then the command would be something like:

```
tar -cf tests.tar /mnt/250GB/tests
```

(to make a tarball called "tests.tar" containing all the files and subdirectories of /mnt/250GB/tests). You can then compress the archive with a command like:

```
bzip2 tests.tar
```

---

### Post by DejitaruJin on 2009-08-26
I may have found the real problem - its own built-in verification process was not programmed to account for the fact that the leading "/" is removed so... well, basically it will always fail, no matter what. And it gives a warning of this, too, but I'd rather have it fixed than just a warning that it's broken XD

I'm going to see if it actually compressed them properly, at least, and go from there.

EDIT: Yup, danwood76's solution worked. Because I wasn't in the root directory, it was still throwing errors at me that it couldn't find the files, but this time it was because it was looking in the wrong place, not because spaces were involved :)

---

### Post by The Cog on 2009-08-26
From man tar:
> 
       -P, --absolute-names
              don’t strip leading ‘/’s from file names

Or this might be another solution:
> 
       -C, --directory DIR
              change to directory DIR


---

### Post by e24ohm on 2009-08-26
> **DejitaruJin said:**
> Okay, I have RAID working (I hope), and I intend to use it. Unfortunately, it seems I need some help with the tar command. I mean, I'm just trying to do what half the servers in the world must be doing, but the tar command doesn't make it easy, and it seems there's little information on the subject.

First and foremost, these are Windows files. Spaces and lengthy filenames abound. This is where the main complications come from. To cover this, I would normally tell it to backup something along the lines of "*", or "/mnt/250GB/tests/*". But it gets very confused by the wildcard.

I've tried passing the data through ls and find, but the result still isn't something tar can readily use. Adding something like `find "/mnt/250GB/tests/*"` *still* interprets the * literally. Moving the quotes outside of the ` for some reason interperets the whole output as a single line. Without the quotes, the spaces cause the same problem as originally.

How in the heck do I make this work?This link from Red Hat should help you out.

[http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/getting-started-guide/s1-zip-tar.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/getting-started-guide/s1-zip-tar.html)

---

