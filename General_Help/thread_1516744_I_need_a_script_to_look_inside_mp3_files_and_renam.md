---
title: "I need a script to look inside mp3 files and rename them."
date: 2010-06-24
forum: General Help
---

### Post by philinux on 2010-06-24
I got a lot of photorec recovered mp3 files. Accidental erasure.

So the file names are now random e.g. f0272384.mp3

If I play a file the track info is displayed in the playlist pane. 

So how do I interrogate the mp3 file for this info and use it to rename the files?

**[edit] **made a start with this. I've found and install eyeD3.

eyeD3 --rename="%A - %a - %n - %t" $file

---

### Post by philinux on 2010-06-24
Solved, good old google, eventually.

```
for file_name in `ls *.mp3`
do

eyeD3 --rename="%A - %a - %n - %t"  $file_name

done
```

---

### Post by DaithiF on 2010-06-24
Hi, just a small point -- no need for backticks and ls, use shell expansion instead: **for file_name in *.mp3**.  If your filenames had spaces (i guess not in this case), you would have problems using the first approach.
([http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.60ls_.2A.mp3.60))

---

### Post by sisco311 on 2010-06-24
EDIT: as DaithiF pointed it out the `ls *.mp3` part is redundant:
```
for file_name in *.mp3 do
  whatever
done
```

But eyeD3 accepts multiple files/directories as arguments:
```
eyeD3 --rename="%A - %a - %n - %t"  *.mp3
```or
```
eyeD3 --rename="%A - %a - %n - %t"  path/to/dir
```

NOTE: On the off chance that the PATTERN (artist,author...) of two or more files is the same, eyeD3 will overwrite existing files without a warning.

---

### Post by philinux on 2010-06-24
Cheers guys. Thanks for the info. 

There were no spaces in the file names as they were all in the format f23423333.mp3 from photorec.

I recovered 40 gig.

---

