---
title: "howTo find &amp; delete (or copy) all files of a type in a directory and all sub dirs ?"
date: 2009-08-28
forum: General Help
---

### Post by MoonRocketZero on 2009-08-28
Hi all I'm new here, and although I have played around with different flavors of linux for over 10 years I am still not great at it so bear with me here, I just completely moved over to Ubuntu on my home systems and so far alls well but I've been trying to figure out how to do these two things for a while, let me try to explain my goals:
[B]
My first question:[/B]

lets say I have a directory in my home dir called "Test", and it has sub directories called "A", "B", "C", "D", etc, etc. (many, many, different sub dirs)

From within the terminal how would I find all files of certain type (for instance *.zip, *.rar, or *.jpg, etc) in the main dir and all it's sub dirs and then rm or srm them all in one step?

For deleting the files with rm (or srm) I found this command: 
```

find -type f -name "*.rar" -exec rm -f {} \; 
```this seems to work but I'm not so sure what all is going on here. I understand the find part, and the rm part I'm just not sure what is sending the find results to rm - what's the deal with the {} \; at the end of the command? and what is -exce telling it to do (execute rm?) if someone could help me understand this a bit more that would be sweet. And also is this the best way to do what I want to do or is there another way?

Also in that instance how would I rm files of two or more different types at the same time (say both *.zip files AND *.rar files in the same command)?

**My second question, which is similar: **

how would I find all files of certain type or types (for instance *.zip, or *.jpg, etc) in "Test" and all it's sub dirs, and then either copy and or (preferably) move them to another directory ?

Any help would be cool. I hope this questions wasn't too long and if I put this in the wrong place sorry, I wasn't sure where to ask in the forums for sure (so just lmk - if I screwed up) Thanks.

---

### Post by exutable on 2009-08-28
Sorry buddy can't really answer you on the first one but for the second one, enter this into a bash script and it should accomplish what you want.  Of course add more lines as it applies:

```

#!/bin/bash
mv *.rar ~/Desktop
mv *.txt ~/Desktop

```

---

### Post by DaithiF on 2009-08-28
Hi,
> what's the deal with the {} \; at the end of the command? and what is -exce telling it to do (execute rm?)-exec is a parameter which tells the find command to EXECute a certain command on each thing it finds.  The thing matched by find is represented in that command by {}.  Finally the \; indicates the end of the command that you want find to exec.

If you want to match 2 different file types you could do it a couple of ways -- easiest would be to do it 2 separate passes, just changing the extension each time.
Or, at the risk of over-complicating things, you can tell the find command to find either type in one pass:
```
find .  \( -name '*.zip' -o -name '*.rar' \) -exec rm -f {} \;
```Warning:  I would always try these commands in a 'safe' way first, by leaving off the -exec piece.
```
find .  \( -name '*.zip' -o -name '*.rar' \) 
``` This will show you the files that are being matched.  Once you are happy that these are what you expect, then you can add the -exec piece to delete, move, or whatever.

To move or copy the files, just replace the rm-f piece like so:
```
find .  \( -name '*.zip' -o -name '*.rar' \) -exec mv {} /path/to/move/to/ \;
```

---

### Post by StuartN on 2009-08-28
Type "man find" in a terminal window for all the many options to this useful command. The example you gave finds all entries of type file ("-type d" would list directories) with names matching the pattern *.rar, and then executes the given command on the matching files indicated by {}.

The default action is -print, list all filenames. An alternative action is -delete, which is much simpler then the -exec rm version. The -ok option is -exec but will query the user for each matching file.

If you are doing this kind of thing infrequently, or doing a wide variety of this kind of operation, then find could be a risky way of doing it. A dual-pane file manager like krusader or gnome commander can run a search and return a list of all matching files in a gui.

---

### Post by MoonRocketZero on 2009-08-28
Thanks for the replies, very helpful.

Special thanks to DaithiF, for explaining the command to me and the other ideas you posted. 
I like to know exactly what a command I type in is doing and your explanation was just what I needed, so thanks! - I will be sure to be careful and test the suggestions you made iin a 'safe' way first before I use them on anything.

Thanks again :)

---

### Post by exutable on 2009-08-28
Now I feel like a total noob

---

### Post by credobyte on 2009-08-28
> **exutable said:**
> Now I feel like a total noob

This feeling resides in temp folder ( it'll disappear faster than you'll be able to make a backup ) :p

---

