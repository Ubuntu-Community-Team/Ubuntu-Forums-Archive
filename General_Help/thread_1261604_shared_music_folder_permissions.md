---
title: "shared music folder permissions"
date: 2009-09-08
forum: General Help
---

### Post by blur xc on 2009-09-08
I screwed them all up and I don't know an easy way to fix them.

The folders should be "rwxrwsr_x"? (775 + the sticky bit?), and the music files should be "rw_rw_r" (664, right)?

Well, my wife ripped some cd's from her user and I assume I forgot to fix her umask value to 002, because the group permission for the files she created were read only.  I, unwittingly "sudo chmod -R 664 Music" to the whole folder structure, thus removing execute permissions to all the directories, taking away my permissions to view the contents.  I was a bit shocked to see all my music disappear from Rythmbox!

So, in my sorry attempt to fix this, I did a "sudo chmod -R 775 Music", but now all the music files have execute permissions which I don't think is right.  So- how do I, in one fell swoop change the permissions on the music files to 664 while keeping the permission on all the directories (and nested sub directories) 774 or 775 (doesn't really matter for the others, because on our system there are no other users...).

Thanks,
BM

---

### Post by Vaphell on 2009-09-08
combination of find and chmod

```
find . -name \*.mp3 -print -exec chmod 664 {} \;
```

in this case search in current dir and below anything with mp3 extension, list it in console and apply chmod 664 to it

find is quite powerful, i guess there are more ways to skin the cat

---

### Post by blur xc on 2009-09-09
> **Vaphell said:**
> combination of find and chmod

```
find . -name \*.mp3 -print -exec chmod 664 {} \;
```in this case search in current dir and below anything with mp3 extension, list it in console and apply chmod 664 to it

find is quite powerful, i guess there are more ways to skin the cat

Worked like a charm...  I ran it again for all the *.jpg cover art files, and then I modified it to remove all the desktop.ini files that copied over from the windows machine they came from.

I'm still interested in other solutions if they are available.  Like, conversely, what if I just wanted to change the permissions all on the directories and subdirectories while leaving all the permissions on the files in the directories alone?

Also- can you explain the syntax for that command?  I'm a student of the command line, and the more I know, the less I need to ask on the forums.  

Find . looks in the current directory?  Why \*?  Is that the whole escaping the wild card thing?  What's the -print option used for?  and why end it with a \;?

Sorry for all the questions, I'd just rather be taught to fish than have one thrown at me. :D

Thanks!
BM

edit:  For the future, should I do a "chmod -R g+w /home/shared" for all the files, if any end up in the shared folder w/o group write permissions?  That wouldn't mess anything up, would it?

---

### Post by Vaphell on 2009-09-09
to be honest i just looked at find help and googled a bit :)

i combined the knowledge of few pages ad voila :)
[http://www.cyberciti.biz/faq/howto-apply-conditional-recursive-chmod-file-permissions/](http://www.cyberciti.biz/faq/howto-apply-conditional-recursive-chmod-file-permissions/)
[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)
especially 2nd one gives detailed info

commands usually support -help or --help parameter - this can give you the idea of available options. Find has an awful lot of possible parameters to say the least.

. = current dir, just like .. = parent dir and ~ = home dir, these are the standard aliases usable by any command
\* is about escaping indeed, 2nd page describes why

it appears **find -type d** lists directories and **find -type f** - files

---

### Post by nothingspecial on 2009-09-09
Have a look at this excellent [[COLOR="Magenta"]introduction to find[/COLOR]]("https://help.ubuntu.com/community/find")

---

### Post by blur xc on 2009-09-09
Thanks for those links!  They are very informative...

BM

---

### Post by nothingspecial on 2009-09-09
Read any tutorials and posts by andrew46 you can find.

He really does know what he`s doing and, more importantly, has the ability to explain things in a way anyone can understand.

So don`t thank me, thank him. He`s the one who took the trouble to write that part of the documentation.

---

