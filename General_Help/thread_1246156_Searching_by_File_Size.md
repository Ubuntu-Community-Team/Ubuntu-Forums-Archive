---
title: "Searching by File Size"
date: 2009-08-21
forum: General Help
---

### Post by alligoodw on 2009-08-21
Using Nautilus, how do I do a search based on file size?  I'm looking for a file that's very large, but I don't know the name of the file.

---

### Post by PGScooter on 2009-08-21
I don't know how to do that with nautilus. You might want to do some searching for a "nautilus script".

I know you specifically said using nautilus, but I can't help but try to give you the command line approach:
```
find ./ -size +100M
```

the ./ means search the current directory (I think this is actually the default), but you could change that to any directory.

Good luck and post back if you find a way to do it in nautilus!

---

### Post by gldearman on 2009-08-21
PGScooter beat me to it, but, yeah, that's the best way to do it.

```
find . -size +100M
```

Of course, you could substitute "100M" out for a different size (good units  to use are k, M, and G).

I'd also like to clarify that using "." as the path, as I've done above, searches the current directory, and also searches all subdirectories recursively.  So, if the current directory is your home, you will search everything in your home directory, even if it's buried in several layers of subdirectory.

I'd also like to clarify that the find command will, of course, return the full path to the file.

If you need more info, type ```
man find
```

find is one of the most powerful tools available in Ubuntu, so learning to use it fully will make your life much better.

---

### Post by PGScooter on 2009-08-21
> **gldearman said:**
> 
find is one of the most powerful tools available in Ubuntu, so learning to use it fully will make your life much better.

I agree! I put off starting to learn it for far too long.

---

### Post by P4man on 2009-08-21
nothing against the command line, but you can also use a GUI for this.
Places > search for files

click the "select more options" . add the "size is at least" option. Then enter the size...

---

### Post by credobyte on 2009-08-21
> **gldearman said:**
> PGScooter beat me to it, but, yeah, that's the best way to do it.

```
find . -size +100M
```Of course, you could substitute "100M" out for a different size (good units  to use are k, M, and G).

I'd also like to clarify that using "." as the path, as I've done above, searches the current directory, and also searches all subdirectories recursively.  So, if the current directory is your home, you will search everything in your home directory, even if it's buried in several layers of subdirectory.

I'd also like to clarify that the find command will, of course, return the full path to the file.

If you need more info, type ```
man find
```find is one of the most powerful tools available in Ubuntu, so learning to use it fully will make your life much better.

IMO, no matter in what style you define your current directory ( . or ./ ), it'll search for files recursively.

---

### Post by gldearman on 2009-08-21
> **credobyte said:**
> IMO, no matter in what style you define your current directory ( . or ./ ), it'll search for files recursively.

You're right.  I hadn't noticed that PGScooter had included the slash, and thought we had listed the same command.  Yeah, "." and "./" define the same path.  What I really wanted to emphasize was that this was a recursive search -- you don't have to especially tell it to search all subdirectories; it will automatically.

---

### Post by kendoori on 2009-08-22
Took a bunch of searching, but this did the trick

[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

The search gui worked very fast, but it didn't allow for deleting from the results list. I had previously installed Dolphin for some reason, and that worked like a charm, including being able to delete the results.

[http://packages.ubuntu.com/jaunty/kde/dolphin](http://packages.ubuntu.com/jaunty/kde/dolphin)[]("http://pcmanfm.sourceforge.net/")

---

