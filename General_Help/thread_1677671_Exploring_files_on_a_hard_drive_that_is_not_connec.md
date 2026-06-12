---
title: "Exploring files on a hard drive that is not connected"
date: 2011-01-29
forum: General Help
---

### Post by oldmankit on 2011-01-29
I don't know if this has been answered before because I don't know what to search for.

I have an external USB hard drive with two partitions, one for backups and one to store large media files (e.g. videos).  I have a laptop so it's only plugged in when I need it.

Is there a way that I can 'see' the files that are on the hard drive even when it's not plugged in?  I am thinking of before deleting a file, I want to check that there is a backup somewhere on the external hard drive.  It would be awesome if I could explore the external hard drive and see a list of "offline" files which I can't access until it's plugged in.  

Is this possible? Does it have a name?

In photographic workflow software there is definitely a way to do this.  I'm thinking more in terms of nautilus though.

PS: Every time I do my backups I use a script (using rsync), so if there is  something I could incorporate into that script I'd be willing to try it.:popcorn:

---

### Post by ragtag on 2011-01-29
```
tree /media/yourusbdrive > ~/filelist.txt
```

Will create a text file listing all the files and folder hirarchy on your drive. Just replace /media/yourusbdrive, with the path to your drive. You won't be able to browse it in Nautilus, but you can view the list and search through it in any text editor.

---

### Post by TeoBigusGeekus on 2011-01-29
Before you unplug your drive, you can do a 
```
ls -RSsha>~/Desktop/filelist.txt
```
and then search the file with your favourite text editor (or simply with grep).

---

### Post by coldraven on 2011-01-29
Alternatives to "Where is it" which does what you want but only in Windows.
I've not tried any of these but the first in the list seems popular.
[http://alternativeto.net/software/where-is-it/?platform=linux](http://alternativeto.net/software/where-is-it/?platform=linux)

---

### Post by oldmankit on 2011-01-30
Great suggestions.  Thanks people.

I tried tree and the ls with options.  They will both serve the purpose and are easy to tag onto the end of my backup script.

I tried one of the GUI things but found it clunky, so will stay simple.

Thanks again.:guitar:

---

