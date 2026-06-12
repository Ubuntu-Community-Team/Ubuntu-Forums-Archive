---
title: "rsync include/exclude issues"
date: 2010-01-27
forum: General Help
---

### Post by dreamspy on 2010-01-27
Hi

I'm trying to sync two directories and the include/exclude function doesn't seem to be working for me. This is my command: 

rsync -rlptv --stats --progress --include='*.mp3' --exclude='*' <sourcedir> <destination dir>

Now the vital part here is the 

--include='*.mp3' --exclude='*' 

From what I have heard then this should include only mp3 files and exclude everything else, but it's just excluding everything.

But if I do like this:

--exclude='*.mp3'

then that actually works, it excludes all mp3 files.

Does anyone know what the proper syntax should be to include some pattern and exclude everything else?

---

### Post by Lars Noodén on 2010-01-27
The pattern I have that copies just the files with a specific filename extension is like this:

```

rsync -a --include='*.mp3' --exclude='*' <sourcedir> <destination dir>

```

---

### Post by dreamspy on 2010-01-27
That isn't working for me either.

But I'we found out what was wrong.

The thing was that rsync wasn't diving into all the subdirectories which were containing my files. If I'd point it to a directory which actually contained mp3 files in it's root then the command worked.

So what I had to do was to include all directories, so I had to change the command to:

rsync -av --include='*/' --include='*.mp3' --exclude='*' <sourcedir> <destinationdir>

so it was that --include='*/' part that did the trick.

Later
Frímann

---

