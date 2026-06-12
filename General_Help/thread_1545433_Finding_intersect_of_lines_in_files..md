---
title: "Finding intersect of lines in files."
date: 2010-08-03
forum: General Help
---

### Post by undecim on 2010-08-03
I have several text files that list hundreds or thousands of words each. I need to find the intersect of each of these sets. (i.e. print only lines that occur in each file) Is there a CLI utility that can do this?

EDIT: Sorry, confused union and intersect. I need to find the intersect.

---

### Post by oaxacamatt1 on 2010-08-03
Hi U,
I believe grep can help you but I would have to look up some other commands and their options.

Try this first:
[http://manpages.ubuntu.com/manpages/lucid/man1/grep.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/grep.1.html)

grep --count --invert-match [pattern] [files] 
or
grep -c -v [pattern] [files] 
These two identical commands should count the lines dont match your given pattern.

[http://manpages.ubuntu.com/manpages/lucid/en/man1/cmp.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/cmp.1.html)

cmp (compare) is sometimes useful for me:  cmp -s oldfile newfile && echo 'no changes'
prints 'no changes' if the two files are the same.

There is also diff and diff3. 
[http://manpages.ubuntu.com/manpages/lucid/en/man1/diff.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/diff.1.html)
 
HTH
M

---

### Post by David Andersson on 2010-08-03
If the files are sorted "comm" can do that. Comm recognizes lines as 1) existing in file1 only, 2) existing in file2 only, or 3) existing in both file1 and file2. There are options to tell it what to output.

To find intersection of 2 alphabetically ordered files:

```
comm -12 file1 file2
```

To find intersection of 2 unordered files:

```
comm -12 <(sort file1) <(sort file2)
```

To find intersection of 3 ordered files, just link two comms together:

```
comm -12 <(comm -12 file1 file2) file3
```

And 3 unordered files:

```
comm -12 <(comm -12 <(sort file1) <(sort file2)) <(sort file3)
```

If there is a variable number of files to intersect, it is probably easier to use temporary files than <(...).

(Note: commands not tested, beware of spelling and logical errors)

---

### Post by undecim on 2010-08-03
> **David Andersson said:**
> If the files are sorted "comm" can do that. Comm recognizes lines as 1) existing in file1 only, 2) existing in file2 only, or 3) existing in both file1 and file2. There are options to tell it what to output.

To find intersection of 2 alphabetically ordered files:

```
comm -12 file1 file2
```

To find intersection of 2 unordered files:

```
comm -12 <(sort file1) <(sort file2)
```

To find intersection of 3 ordered files, just link two comms together:

```
comm -12 <(comm -12 file1 file2) file3
```

And 3 unordered files:

```
comm -12 <(comm -12 <(sort file1) <(sort file2)) <(sort file3)
```

If there is a variable number of files to intersect, it is probably easier to use temporary files than <(...).

(Note: commands not tested, beware of spelling and logical errors)

Thanks! It took some more scripting in order to do this with as many files as I had, but I got it!

---

