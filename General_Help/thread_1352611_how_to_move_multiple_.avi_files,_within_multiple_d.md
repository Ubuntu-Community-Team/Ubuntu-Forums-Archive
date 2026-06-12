---
title: "how to move multiple .avi files, within multiple directories, within a directory :)"
date: 2009-12-11
forum: General Help
---

### Post by switch10 on 2009-12-11
I've been google seaching all day for the answer to this.  I'm going to explain myself the best I can..  This is an example by the way...

I have a directory called videos.  Within that directory there are several other directories, all containing an .avi file.  I want to either move, or copy all of these .avi files to another location with one command.

so here is what I have so far..  This has to be possible.  I know I'm missing something I just don't know what.

```
mv *.avi /media/disk/videos
```

Any help would be much appreciated.

Thanks

Dave

---

### Post by switch10 on 2009-12-11
hmm how would something like this work??

```
find . -name *.avi -exec cp "{}" /<dir> \;
```

---

### Post by switch10 on 2009-12-11
never mind.  Im missing something still..

Im getting this...

```
find: missing argument to `-exec'
```

---

### Post by kaibob on 2009-12-11
I belive *.avi has to be quoted. Try the following:

```
find . -name '*.avi' -exec cp '{}' /target/directory \;
```

I tested the above and it does work. Be sure you are in the top-level source directory when you execute the command. Or, as an alternative, replace, the . after find with the path to the source directory. Two additional thoughts. You may want to use -iname rather than -name if any of the source files have upper case extensions. Also, you may want to use the --backup=numbered option with the copy command to avoid files with the same names overwriting one another. 

BTW, you live in a pretty place. Are you getting any snow?

---

### Post by switch10 on 2009-12-11
Thank you!!  that worked perfectly!!!

---

### Post by gomyhr on 2009-12-11
Isn't this the simplest way of doing it?

```
mv */*.avi /media/disk/videos
```

Unlike the find command is supposes that the avi files are exactly one directory level under the current one, but isn't that your situation?

---

### Post by switch10 on 2009-12-11
> **gomyhr said:**
> Isn't this the simplest way of doing it?

```
mv */*.avi /media/disk/videos
```

Unlike the find command is supposes that the avi files are exactly one directory level under the current one, but isn't that your situation?

Wow this came in handy as well!!  is there a way I can go more than one directory level under the current one using a similar command??

I tried more slashes, but that didnt work..

Thank you for the help

---

### Post by switch10 on 2009-12-11
> **switch10 said:**
> Wow this came in handy as well!!  is there a way I can go more than one directory level under the current one using a similar command??

I tried more slashes, but that didnt work..

Thank you for the help

Awesome!! I figured it out!!  I've been trying to figure out how to play all my songs with mpg123 in my music directory, which has 3 levels of subdirectories.  this worked great!!

```
mpg123 */*/*/*.mp3
```

Thanks again

Dave

---

### Post by Physical Hook on 2009-12-11
[COLOR=Gray]-- nvm --[/COLOR]

---

