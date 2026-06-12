---
title: "Rename multiple files"
date: 2006-02-09
forum: General Help
---

### Post by nik on 2006-02-09
Alright, I have several files in a folder, and I want to remove some part of the filename on all (same part). Exampel:
file1something.jpg
file2something.jpg
file3something.jpg
and I want to remove something from all the files. Any easy ways to do that?

---

### Post by jrib on 2006-02-10
rename command.  Easy if you know regular expressions.  If not, a quick tutorial you find on google will get you going in no time (with the basics anyway).  It's not difficult, just spend a few minutes reading through a tutorial.

In your example, to get rid of something you would do:

```
rename 's/(file[0-9]*).*(\.jpg)/$1$2/' *
```

I know that looks a little complicated, but regex are a good thing to know and you'll feel so powerful after running a command like that to do what you want :)

---

### Post by geekphreak on 2006-02-10
If you have way too many files to rename, and want a GUI interface, take a look  programs such as KRename.

---

### Post by bountonw on 2006-02-10
Wow, I haven't even mastered bash and now they're throwing regex at me.  Just found this tutorial to work through.  Sounds like fun.  Thanks for giving a word to google.  

[http://www.regular-expressions.info/tutorial.html](http://www.regular-expressions.info/tutorial.html)

---

### Post by nik on 2006-02-10
Thanks all. I would like a gui, but I suppose it's time well spent to learn the basics of regular expressions... I'll try the link and read up on it :)

bountonw, I feel the same way... Still, the beauty of linux, right? Learning something new every day :)

---

### Post by robenroute on 2006-02-10
Krename is for KDE, so if you don't want to install loads of KDE libraries, just use a program called 'wildcard' (it's for Gnome).

Good luck

---

### Post by lol on 2006-02-10
There is a gnome tool as well, 'prefixsuffix', but it is quite limited.

But if you want to rename pictures, you can also use tools like gqview. Most of them have a feature 'rename series...' of something like that (it may even be possible to use it with any kind of files).

---

### Post by cotcot on 2006-02-10
You can also group rename in gthump (photo viewer under gnome).

---

### Post by bountonw on 2006-02-14
As I said in an earlier post in this thread, [http://www.regular-expressions.info/tutorial.html](http://www.regular-expressions.info/tutorial.html) is a good guide to regular expressions.

I also found that typing ```
man regex
``` gives a rather technical (read difficult) explanation of the regular expressions used in bash.

I have read through these.  Still a lot of Greek in there.  Simple question.  I have three files and want to move them to a different directory. 

exit
exit.s
exit.o

I could have done it with a gui in three seconds.  I also could have moved them one by one in 20 seconds at the command line.  As it is, I have been at it for an hour reading the above info and trying different combinations hoping to make them all go at once.  This is a learning opportunity for me to hopefully help me understand things better and also to be able to work faster from the command line in the future. 

I normally dwell in the absolute beginners forum, but drifted to this forum through the search.

---

### Post by lol on 2006-02-14
You won't find answer to this question in 'man regex', but rather in 'man bash', section EXPANSION.

Now depending on the files present in your directory, several command lines could produce the correct result (I use ls in my examples rather than mv, but it is the same):

```

ls exit*
ls exit exit.*
ls exit{,.o,.s}
ls exit{,.?}
ls exit?([.])?([os])
ls @(exit?([.])?([so]))
ls exit exit.o exit.s

```
Those are actually only examples, I am not sure that they are fully correct, and they don't procude exactly the same results depending on the files in the directory. You can probably build a few dozen other examples like this.

Anyway, the safest way to do this is the last one, and I am sure it doesn't takes more than a few seconds to type this command line (with the help of tab, probably no more than the time needed to select the files in a GUI).

---

### Post by bountonw on 2006-02-14
Thank you.  With your help I typed.

```
mv exit* ~/Desktop/practice
```

All three files moved.  My problem was trying to do it outside the folder.  When I was in ~/Desktop/practice I tried different combinations of 

```
mv ~/Desktop/exit* .
```

I received an error message that the directory or file ~/Desktop/exit* did not exist.

Anyway, now that I can do it, I have moved it around several files and back just to say that I could.  Thank you lol for pointing this out.  One more thing that I can do.  Just 16,973,285 more to go.

---

