---
title: "commands for batch deleting folders/files by name/type?"
date: 2011-05-18
forum: General Help
---

### Post by Knacker on 2011-05-18
Hi,
I'm trying to clean up a few hundred thousand mp3 files and I'm dying to find a way to automate some of the mechanical tasks I keep doing. It seems like at least two of these tasks could be easily accomplished with something at the command line, but I don't have the chops/know-how to figure out how (and would really rather not trial and error with batch deleting files & folders...). So, can anyone give me some pointers on how to:

1) Delete all folders named "_MACOSX" (and all subfolders/files contained therein)
     -- Basically, I'd like to apply this command to a few hundred directories that may or may not contain a subfolder called "_MACOSX" that I'd really like to get rid of. 

2) Delete all files named "*.m3u".
    -- Similar to the first, I want to automatically scan all directories and subdirectories in a given location for all instances of this file-type and delete them wherever they're found. 

3) Move all files named *.txt", "*.doc", "*.pdf" to a specific location. 
   -- Similar to the last, except instead of deleting, I'd like to just move them, so that if there is anything worth keeping, I can keep it.

Any help with any of these or any general advice would be very much appreciated.

---

### Post by Plueonic on 2011-05-18
1)
```
find /home/user/Music -name "*MACOSX" | xargs rm -r
```2)
```
find /home/user/Music  -name "*.m3u" | xargs rm
```3)
```
find /home/user/Music  \( -name "*.txt" -or -name "*.doc" -or  -name "*.pdf" \) -print0 | xargs -0 -I{} mv {} /home/user/Stuff
```

---

### Post by Knacker on 2011-05-18
> **Plueonic said:**
> 1)
```
find /home/user/Music -name "*MACOSX" | xargs rm -r
```2)
```
find /home/user/Music  -name "*.m3u" | xargs rm
```3)
```
find /home/user/Music  \( -name "*.txt" -or -name "*.doc" -or  -name "*.pdf" \) -print0 | xargs -0 -I{} mv {} /home/user/Stuff
```

Thank you!! This is terrific. More than I had hoped for. 

Just looking at these, I wonder if I don't need a flag to make the second and third recursive...but I can probably figure that out on my own. 

Thanks so much again for this. You've saved me hours of time!

EDIT: all work like a charm! thanks again!

---

### Post by Plueonic on 2011-05-18
Glad it worked out :)

*find* is recursive by default, so if you ever need to make a non-recursive search, you can use the -maxdepth option
```
find ./  -maxdepth 1 *search pattern*
```

---

