---
title: "find mv and create directory structure"
date: 2011-02-06
forum: General Help
---

### Post by fistikuffs on 2011-02-06
Hi there, I'm trying to pull all my flacs out of my Music collection. I can do it with following command
```
find b/ -name *.flac -exec mv {} flac/ \;

```which works great except it moves all the flac files to the flac folder. I want it to recreate the original folder the flacs were found in and mv the files there. essentially recreate directory structure but only folders with flac files. Can anyone help please?

---

### Post by AlphaLexman on 2011-02-06
I tried this briefly, I need your full path to the flac files, and your path to where you want them to go. (Maybe even the path to your $HOME)

---

### Post by fistikuffs on 2011-02-06
> **AlphaLexman said:**
> I tried this briefly, I need your full path to the flac files, and your path to where you want them to go. (Maybe even the path to your $HOME)

Thanks for the reply!
Its on a nas the path i want to search for flac files is 
```
/mnt/Multimedia/MUSIC
``` 

And the destination is 
```
/mnt/Multimedia/MUSIC/flac
```

Also i don't think i explained it very well. I want to find directories containg flac files and move the directories found, including all their files, to the destination directory.

---

