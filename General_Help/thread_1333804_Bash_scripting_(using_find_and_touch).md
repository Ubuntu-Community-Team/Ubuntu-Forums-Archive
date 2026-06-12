---
title: "Bash scripting (using find and touch)"
date: 2009-11-21
forum: General Help
---

### Post by poubelle on 2009-11-21
Hi all,

I have a crappy noname Ipod clone which, as best I can tell, sorts MP3s in their directories by "accessed date", ie, the date the file was put on the player. 

This is annoying, because when I upload entire folders, sometimes the individual MP3s wind up on the player out of sequence. 

So I've been experimenting with the touch command, re-ordering all the files in a given directory. They seem to play in the correct order when I do that.

(My MP3s are in the following format on the player:

/Music/artist/album/tracknumber title.mp3

After going into each album folder under each artist folder, this is getting tedious, so I tried writing a bash script to zap the entire player. This way I can just run a script each time I put stuff on the player.

The only thing is, the scripts I have written do the touch command out of sequence, so everything sorts even worse. For example:

```
#!/bin/bash
find . -print0 | xargs -0 touch
```

This re-orders everything randomly.

```
#!/bin/bash
for i in *; do touch "$i"; done
```

If I run this in the /Music folder, it re-orders the artist directories correctly, but isn't recursive.

```
#!/bin/bash
find -L -name *.mp3; for i in *; do touch "$i"; done
```

Again, this re-orders the artist folders correctly, but isn't recursive. (And isn't find supposed to be recursive by default?)

I'm clearly way off-track here... I'm sure this is simple. Can someone help me?

To be clear, what I need is something that will re-order all files and folders in alpha/numerical order, so that the artist folders are in alpha order, the album folders inside are in alpha order, and the MP3s inside the albums are in alpha/numerical order. 

Thank you!

---

### Post by sisco311 on 2009-11-21
find is recursive but its output is not in lexicographic order.

```
man bash | less --pattern\="globstar"
```

```

shopt -s globstar
for i in **; do touch "$i"; done
```
[/code]

---

### Post by mo.reina on 2009-11-21
have you tried:

```
for line in $(find home/user/Music -name *.mp3); do
      touch $line
done
```

---

### Post by mo.reina on 2009-11-22
sisco311 is right,  you'll have to use the shell's globbing feature.  i guess this is why filenames in *nix systems don't have spaces, lot of hassle.

```
for line in /Music/**/*.mp3; do
    touch $line
done
```

---

### Post by poubelle on 2009-12-14
Ugh, okay, first of all thanks to you all for your help. I'm still having trouble, but I suspect it's the player's problem, not the scripting.

I'm still not sure how the player orders the files. All files in a given directory can have the same accessed time and same modified time, but the player can still list them out of order. The only way I've been able to reliably get the files to play in order is if I drop them one by one onto the player in Nautilus. Obviously this is a time-consuming process, so I've been trying to script a way around this.

I guess my next question is, then, does the fact that dropping files one-by-one in order into the player mean that the setting used to organize MP3s on the player is actually the CTIME? 

And if so, is CTIME still impossible to change?

This is so annoying. Never buy an iPod clone.

---

