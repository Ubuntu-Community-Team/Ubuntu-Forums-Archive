---
title: "Hard links only for all files in directory"
date: 2010-01-15
forum: General Help
---

### Post by Andaril on 2010-01-15
I have a Music folder and I need to create hard links for all files in Music directory.
For example:
~/Music/01 - the song.ogg // hard link for this file
~/Music/Folder/02 - a song.ogg //and for this file TOO!

to
~/Other Music/01 - the song.ogg
~/Other Music/Other foldr/02 - a song.ogg

I want hard link files in folder and in subfolders, but not folders its self.

---

### Post by Andaril on 2010-01-15
Tried ~/Music/*/* but it didn't work...

---

### Post by falconindy on 2010-01-15
This should work...

First, make the directory structures:
```
cd ~/Other\ Music/;find ~/Music -type d | while read dir; do mkdir -p "${dir//*Music\/}"
```

Then make the hard links...
```
cd ~/Other\ Music/;find ~/Music -type f | while read file; do ln "$file" "${file//*Music\/}"; done
```

One has to wonder why you're doing this though...

---

### Post by Portmanteaufu on 2010-01-15
> **Andaril said:**
> Tried ~/Music/*/* but it didn't work...

When you use "*" on the command line, it gets expanded before the command is actually run. That is to say, if you write:

```
ls *
```

then what's **really** being executed is:

```
ls file1 file2 file3
```

...assuming that that folder contains those files. The only reason this works is because "ls" is specifically designed to take any number of command line arguments. If you take something like "ln", the link creator, which only expects 2 command line arguments (a source and a new link name) and you use "*" on the command line, it's going to end up being run with loads of arguments that it doesn't know what to do with.

Did that make sense?

As an alternative, you could write a short script to do this sort of thing. Are you familiar with scripting or would you like assistance?

Also: hard links have some inherent dangers associated with their use. Often times soft links are safer to employ. Is there a particular reason you've decided to use hard links?

---

### Post by Andaril on 2010-01-15
THX!
But I found an easy way!
cp - copy
-r (recursive
-l (hard link, instead of copy)
so :
cp -r -l %source directory% %out direcrory%

---

### Post by falconindy on 2010-01-15
> **Andaril said:**
> THX!
But I found an easy way!
cp - copy
-r (recursive
-l (hard link, instead of copy)
so :
cp -r -l %source directory% %out direcrory%

Learn something new every day...

---

### Post by chitowner2 on 2010-05-17
[FONT="Arial"]Bump!

OK, a related question I think. I also want to create hard links, but only to files that are duplicates, linking to the 'first instance'.

We all know how "new" CD's get released that include tracks from previous issues. Problem is, get a few thousand CD's ripped and you're talking about a serious amount of disk space.

I'm trying to use rsync to scan recursively, identify the duplicate files, and convert them to hard links. Unfortunately rsync is not one of my best skills.  :-/

This seems much preferable to using rsync to simply delete the files, and they are all in a single contiguous directory tree so with the right syntax a command should be fairly simple, right?

CT
[/FONT]

---

