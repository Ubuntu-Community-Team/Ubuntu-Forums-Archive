---
title: "Rename files in subdirectories in command line"
date: 2010-01-15
forum: General Help
---

### Post by kiddykoff on 2010-01-15
I just installed Rockbox on my Ipod and I'm enjoying it. Maybe some of you already know that the ipod firmware asked for albumart to be saved to the mp3 tags of files. This caused artwork to be stored 10+ times. Or in the case of the Bob Marley Songs of Freedom collection 78 times.

Rockbox allows external files to be read as albumart depending on placement and name.

I currently have my albumart set as
..\<Artist>\<Album>\folder(1).jpg

I had been messing around with the rename command in the terminal, but i keep messing up the perlexpr. the tutorials that i've come to for batch renaming assume all the files are in the same directory, but i'm trying to rename files in subdirectories.

Some of you may know that in windows if you select files and rename them they will have the same base name with an incremental number attached. (this is how i ended up with (1), I did a search for .jpg and selected all of them and renamed as folder.)

how can i use the rename command to search for these files and rename as cover.jpg. Without navigating to every single directory.

Thanks in advance if i don't reply soon.

---

### Post by lykwydchykyn on 2010-01-15
I think this will do it, but make a backup copy first just in case I'm wrong (flying blind here, since I don't have your files to test with).

cd to your music directory and do:
```

find ./ -iname "folder(1).jpg" -execdir cp {} cover.jpg \;

```

You could use "mv" instead of "cp" to actually remove the old file, but it's potentially less destructive to use cp just in case my syntax is off.

---

### Post by kiddykoff on 2010-01-15
> **lykwydchykyn said:**
> I think this will do it, but make a backup copy first just in case I'm wrong (flying blind here, since I don't have your files to test with).

cd to your music directory and do:
```

find ./ -iname "folder(1).jpg" -execdir cp {} cover.jpg \;

```

You could use "mv" instead of "cp" to actually remove the old file, but it's potentially less destructive to use cp just in case my syntax is off.

i'll try that out right now. I had been trying
```

rename -n -v 's/././folder(1)$/cover/' *.jpg

```
but something is wrong with my syntax and/or the command is incapable of doing what i want

---

### Post by kiddykoff on 2010-01-15
that didn't work, but it's given me a new area to look into. I'm not a big user of command lines, but i'm feeling it's my best bet for accomplishing this task.

---

### Post by audiomick on 2010-01-15
you might want to look for the option -r  meaning recursive in the man page of the command you are thinking of using.
```
man <*command*>
```
If it is there, it generally says, more or less, "and for all subdirectories"

---

### Post by kiddykoff on 2010-01-15
after reading the manual and figuring out how to insert (,), and spaces. I figured out the correct code. 
```

find ./ -iname "folder\ \(1\)\.jpg" -execdir cp {} cover.jpg \;

```
I hope this helps anyone else out there and thanks to lykwydchykyn

---

