---
title: "I want 8-3 file names!"
date: 2009-08-03
forum: General Help
---

### Post by daenku32 on 2009-08-03
Why? Good question. The *old* MP3 capable CD-Player in my car can't handle long file names very well.

So I need to rename some MP3s to 8-3 file names so that they'll play from a burned CD-R.

Any tips, scripts, to avoid having to rename hundreds of files by hand?

---

### Post by wojox on 2009-08-03
For example rename all *.bak file as *.txt, enter:
```
rename .bak .txt *.bak
```

---

### Post by finch127 on 2009-08-03
hmm i dont know exactly what you are asking for but for whenever i need to rename a bunch of files tediously i use GPrename which I think is in the repos. Maybe you can copy all of the mp3 files to a new directory, use gp rename to give them all generic names (1.mp3, 2.mp3, etc etc) and then use those and delete the directory when finished?

---

### Post by ppirilla on 2009-08-03
Sounds to me like your mp3 player is not compatable with Joliet Extension CD's, so disable that and burn your disc in ISO-9660 / CDFS.  It will automatically convert file names to 8.3, most likely by taking the first six characters and appending ~1, ~2, etc.

---

### Post by kaibob on 2009-08-03
> **daenku32 said:**
> Why? Good question. The *old* MP3 capable CD-Player in my car can't handle long file names very well.

So I need to rename some MP3s to 8-3 file names so that they'll play from a burned CD-R.

Any tips, scripts, to avoid having to rename hundreds of files by hand?

Have a look at pyrenamer. It has many rename options:

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

If you're looking for a command-line solution, that is easily done, but some additional information is needed. First, what do you want as new file names? If the answer is the first 8 letter of the existing file name plus the extension, how do you want to handle duplicate file names.

---

