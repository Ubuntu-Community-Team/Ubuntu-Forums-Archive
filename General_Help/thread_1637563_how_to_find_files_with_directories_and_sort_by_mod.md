---
title: "how to find files with directories and sort by mod time"
date: 2010-12-04
forum: General Help
---

### Post by Lynx Phoenix on 2010-12-04
ok i'm not sure this is the right part of the forum to post this, so if moderation needs to move this thread i'm fine with it. i'm not exactly asking for help per se, more of an opinion and showing how i did this sort thing that maybe others are having a bit of trouble with.

so, what i wanted to do was find all the files with a specific name from a tree, sort them by modification time and have their directory appended to them so that i knew where they were (because they all have the same name). i tried a whole bunch of different things and finally did this:

```
find . -type f -name world.sav -exec ls -l '{}' \; > ~/dfsaves.txt; gawk '{$1=""; $2=""; $3=""; $4=""; $5=""; print}'  ~/dfsaves.txt | sort -n > ~/dfsavessorted.txt
```

this did the trick pretty well, but as you can see it is far from elegant and i think i'm doing some things wrong and kludgy

first thing i tried was "ls -lRt | grep world.sav" which worked except i couldnt distinguish the files because there were no directories. that took a lot of looking till i accepted i couldnt make ls print directories as well and append them to the files somehow that their relationship would be clear. i tried piping ls to find, doing it in reverse, passing them from grep etc. etc. until i read some more stuff online that got me using gawk and sort. the questions:

1. is there some other, more elegant and simple way to do this kind of detection and sorting?
2. is there any way to use a pipe after using exec? the semicolon seems to prevent this entirely, forcing me to use an intermediate file as above. i could just remove it later, but i'd prefer a straight piping.

---

### Post by sisco311 on 2010-12-05
In bash, if the globstar option is enabled, then the pattern **  used in a pathname expansion context will match a files and zero or more directories and subdirectories.  If the pattern is followed by a /, only directories and subdirectories match.

So, you could run something like:
```
shopt -s globstar
ls -lt path/to/dir/**/world.sav > ~/file
```

---

### Post by Lynx Phoenix on 2010-12-05
a shameful but friendly *bump*

---

### Post by SeijiSensei on 2010-12-05
```
ls -ltr $(locate file.name)
```

seems to work for me.

If you just want the full file names:

```
ls -ltr $(locate file.name | awk '{print $8}')
```

---

### Post by sisco311 on 2010-12-05
locate reads the file names from a database which could be outdated. I would use find:
```
find path/to/dir -type f -name file.name -exec ls -ltr '{}' +
```
or
```
find path/to/dir -type f -name file.name -exec ls -1tr '{}' +
```

or find and xargs variant:
```
find path/to/dir -type f -name file.name -print0 | xargs -0 ls -1tr
```

---

### Post by Lynx Phoenix on 2010-12-05
sorry for that bump, bad timing :P apparently i didnt even return to the thread after posting

anyway, sisco's worked perfectly and i learned a new bash thing, which is nice. thanks!

seiji's would probably work but the directories over which i need to search are complicated a bit and full of whitespace so it just throws up a lot of 'no such file or diretory' lines, perhaps sorting the 'world.sav' files underneath but its hard to make sense of the output that way. using the awk extension seems to ignore the filename and just outputs every file. i might have done something wrong but i cant tell. thanks anyway

edit - lol strange timing again sisco, your post popped up just when i clicked reply :P the ones you posted work perfectly as well (2nd one seems identical to the 1st though). and they're even more elegant ^_^

thanks to both of you, that was exactly what i needed :popcorn:

---

### Post by sisco311 on 2010-12-05
> **Lynx Phoenix said:**
> (2nd one seems identical to the 1st though)

They aren't. The first one uses ls -l (lowercase L = use long listing format), while the second one uses ls -1 (one = list one file per line).

---

### Post by dcstar on 2010-12-06
> **Lynx Phoenix said:**
> 
.........
thanks to both of you, that was exactly what i needed :popcorn:

So it is **Solved**, is it?

---

### Post by SeijiSensei on 2010-12-07
> **sisco311 said:**
> locate reads the file names from a database which could be outdated.

On my Ubuntu machines, the database is updated each morning at 6:25 am by a cron job.  These are pretty vanilla installations, so I'd assume that's true for most other users here as well.  If you're looking for files newer than 6:30 am, you'll need find.  Otherwise locate is much faster.

If you need to force a database update, just run "sudo updatedb" before searching.

Those "cannot access" errors from ls have to do with files with embedded spaces in their names.  Try this instead:

```
ls -ltr "$(locate file.name)"
```

---

