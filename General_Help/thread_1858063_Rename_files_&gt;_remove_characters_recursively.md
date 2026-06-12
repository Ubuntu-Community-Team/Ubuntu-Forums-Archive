---
title: "Rename files &gt; remove characters recursively"
date: 2011-10-11
forum: General Help
---

### Post by philmjones on 2011-10-11
I'd like to rename many (hundreds, if not thousands) of files in my music collection, but not the directories themselves.

My music collection is organised in directories (artist > album) and some stupid software has added the track number to each file, like this:

01 track name.mp3

I want to remove the "01 [space]". I've tried using Thunar but have to select the files in each directory manually, a job that's going to take me an age. I'm not confident enough to try messing with scripts in the terminal since I don't really know what I'm doing. Is there a simple script that can strip out the unwanted characters from the filename, leave the directory name intact, then move on to the next directory?

Thanks.

---

### Post by vanadium on 2011-10-11
I would use Easytag for this job, but that would require that the tags of your audio files are properly filled.

With "rename" you could strip the trhee first characters from a file:
```

rename 's/^...//' <yourmp3file>

```

This command could be repeated for all files in a directory and beneath using find:
```

find <wheretostart> -name "*.mp3" -execdir rename 's/^.....//' "{}" \;

```
Five first characters are removed, because find returns the filenames as "./filename.mp3".

Be sure you have a backup copy before you try this, and first test on a small bunch of files. Shell operations like these can be mighty, but are oh so dangerous.

---

### Post by philmjones on 2011-10-13
Thank you @vanadium, that worked beautifully.

---

