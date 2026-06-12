---
title: "Adding tags to the FLAC files"
date: 2010-04-16
forum: General Help
---

### Post by Konbuntu on 2010-04-16
I'm following a tutorial which tells me the following:

You will need "cuetag" for this which is part of the "cuetools" but since you already installed it (see previous seps), all you have to do is open the terminal, navigate to the folder where you just splitted some APE or FLAC files and type this:

```
cuetag *.cue split-track*.flac ;
```


(if you didn't change the file's name from split-trackNN.flac). All the split-track*.flac files will have tags in just a few seconds.

so i did exactly what i was suppose to do but for some reason is still could not add the tags to my FLAC files..

```
kon@kon-laptop:~$ cd ~/Desktop
kon@kon-laptop:~/Desktop$ cd *ora*
kon@kon-laptop:~/Desktop/sDvorak $ cd *CD1*
kon@kon-laptop:~/Desktop/sDvorak /CD1$ cuetag *.cue split-track*.flac ;
kon@kon-laptop:~/Desktop/sDvorak /CD1$ cuetag *.cue split-track*.flac ;
kon@kon-laptop:~/Desktop/sDvorak /CD1$ 

```

anyone?

=/

---

### Post by darolu on 2010-04-17
I use [easytag]("http://packages.ubuntu.com/karmic/easytag") to edit my FLAC files' tags, maybe it will work for you too.

---

### Post by mc4man on 2010-04-17
The  dir. on your desktop "sDvorak" probably has a space after the k, ie. - sDvorak<space> (you can inadvertently add a space to a name, either in front or at end

So now your prompt's path has a space that may  be an issue for cuetag

```
kon@kon-laptop:~/Desktop/sDvorak /CD1$
```

Maybe try renaming sDvorak<space> back to sDvorak, the prompt should be
```
kon@kon-laptop:~/Desktop/sDvorak/CD1$
```

---

