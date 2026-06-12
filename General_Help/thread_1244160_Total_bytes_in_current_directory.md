---
title: "Total bytes in current directory"
date: 2009-08-19
forum: General Help
---

### Post by Pi72 on 2009-08-19
Hi people!

Well, I've been using Ubuntu for about a year, but I'm still a bit green in the command line usage.

What I'm trying to do is count the total number of bytes of files in a certain directory (f.e. the current one) including files in subfolders (recursively).

Note that I don't want to know how much they occupy in the disk, nor the apparent compressed bilateral block size. I want their size.

Let's see a simple example with the closest thing I've found. A folder with a single file of 2914 bytes. I issue "du -b -s ." and it says 7050 bytes.

Another example, a tree with subfolders and files in it. Counting files individually it gave me 515,765,120 bytes. "du -b -s" which supposedly should use a block size of 1 byte and give the apparent size and not the size it uses in disks, gives 515,785,600. The error is minimal, but it doesn't help me for my needs.

I also found a simple bash script which supposedly does that too, starts with:
for Bytes in $(ls -l | grep "^-" | awk '{ print $5 }')
do
   let TotalBytes=$TotalBytes+$Bytes
done

But it didn't serve my purposes either (couldn't make it work properly, not to talk about making it recursive...)

So, please, any ideas? Thanks in advance.

---

### Post by MartinEve on 2009-08-19
I'm pretty sure that, regardless of your trouble you'll want to use du (DiskUsage).

The h switch prints in human readable form.
The s switch prints only a summary.
It can take a directory as an argument:

```
martin@theoria:~$ du -hs Music
292G    Music
```

Where "Music" was a subdirectory of my home folder.

```
martin@theoria:~$ du -s Music
305253548       Music
```

```
martin@theoria:~$ du -bs Music
312162289008    Music
```

If it's displaying the wrong count, it would be a bug in du, which seems highly unlikely...

Hope that helps.

Martin

---

### Post by DaithiF on 2009-08-19
Hi, any hidden files in those directories that you may be missing when counting individually?

one way to do this recursively would be:
```
find . -type f -print0 | wc -c --files0-from=-
```
which will calc # of bytes for each file, and an overall total

---

### Post by Pi72 on 2009-08-19
Thanks Daithi! The findy thing was exactly was I was searching for. It gives the exact result I need. You saved me from a big headache!

---

