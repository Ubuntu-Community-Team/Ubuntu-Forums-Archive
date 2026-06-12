---
title: "Problem with java command line arguments"
date: 2009-08-19
forum: General Help
---

### Post by manneorama on 2009-08-19
Hi all,

I'm not sure if this is the correct place to start this thread, but I found none better so here goes:

Scenario:
I have a compiled .jar-file that I wish to run. This particular application takes the argument vector (which happens to be an sql-ish statement) and tries to parse it. If you haven't guessed already I'm writing an application that enables MySQL-style statements in a regular terminal window. But anyway, back to the problem. Running a .jar, that's easy enough.

```

emanuel@dominator:~/Code/Netbeans/Select$ java -jar dist/Select.jar select * from /usr/lib
DBG-0: Parsing query: 
[INDENT]**selectbuild build.xml dist manifest.mf nbproject src test from /usr/lib**[/INDENT]
Fatal: run called on faulty task.

```

Now **THAT** is not what I wrote on the command line! And the same thing happens when I try to run the .class-file.

But let's see, where does those weird extra strings come from?

```

emanuel@dominator:~/Code/Netbeans/Select$ ls -l
totalt 28
drwxr-xr-x 3 emanuel emanuel 4096 2009-08-20 00:13 **build**
-rw-r--r-- 1 emanuel emanuel 3639 2009-08-20 00:03 **build.xml**
drwxr-xr-x 2 emanuel emanuel 4096 2009-08-20 00:13 **dist**
-rw-r--r-- 1 emanuel emanuel   82 2009-08-17 20:01 **manifest.mf**
drwxr-xr-x 3 emanuel emanuel 4096 2009-08-17 20:01 **nbproject**
drwxr-xr-x 3 emanuel emanuel 4096 2009-08-19 23:46 **src**
drwxr-xr-x 2 emanuel emanuel 4096 2009-08-17 20:01 **test**

```

And there's our answer...

Now, I've been scratching my head for the last five hours trying to figure out how the heck this can happen. I've checked my code around a million times. And a code block that takes the command-line argument vector and turns it into a space-separated string is very embarassing to get wrong after five years of developing with Java. So I'm pretty sure thats not it. **AND** the application works just fine when started from within NetBeans. A fact only pushes me closer to a breakdown.

So, any ideas? 
(Please have ideas or I'm going to need hairplugs after the aforementioned breakdown, in which I'll probably put my laptop in the freezer and sit down in a corner, shaking and pulling my luscious brown hair while gently humming old Swedish lullabies)

---

### Post by DaithiF on 2009-08-19
Hi,
the shell is expanding the '*' character into the list of files in the current directory.

you could escape the '*' character like \* to get around this, or depending on how you do your parsing in java you could enclose the whole select statement in quotes

---

### Post by manneorama on 2009-08-20
Oh my, why didn't I think of that? I blame low bloodsugar and ten hours at the office =). Thanks.

---

