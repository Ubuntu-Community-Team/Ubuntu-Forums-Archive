---
title: "Install new software?"
date: 2010-03-09
forum: General Help
---

### Post by tetris11 on 2010-03-09
Hey there,
I just downloaded a large directory via rsync which contains a lot of software that I need to use.

Only trouble is, I cant seem to install it.

It doesn't come with a makefile, and there's a bin folder and everything - looks as if it's already built.

When Im at the uni cluster, I just type in 'dipso' to start the dipso program, but that doesnt seem to work here....

What file do I need to edit so that it knows that new programs have been installed to a different directory?

---

### Post by howefield on 2010-03-09
Are you seriously expecting an answer which resolves your issue with the meagre information you provide ? ;-)

Is this Uni stuff, your admin will likely be able to sort you out ?

---

### Post by tetris11 on 2010-03-09
It is pretty poor information...

Basically, I tried to install some software, so I went to their site, and saw that their latest builds were available via rsync.

So I thought, hey why not. I successfully copied everything into a folder called 'star', but when it came to running anything, it would not recognise any of the programs within the folder.

The current directories/files within star are:
bin           etc       include  lib         manifests  share
buildsupport  examples  info     lost+found  news       starjava
docs          help      java     man         Perl

As you can see, there is no INSTALL or make files.
If I go into the bin folder, I see all the programs I want to run, but even when I double click on them, or type in their filepath in terminal, nothing runs.

So Im wondering if there is anything I need to change in my system, so that it knows that ontop of the /bin folder, there are apps within the ~/star/bin folder too.

Hope I was clearer, ;)

---

### Post by tetris11 on 2010-03-09
Ok so it turns out that I needed to set my environment variables so that the system knew where I the programs were.

I moved everything to / and then editted the ./bashrc file, and then did 'source /star/etc/profile/"

and everything worked.

Kind of. I keep getting "error while loading shared libraries: libexpat.so.0: Cannot open shared object file: No such file or directory"

---

### Post by tetris11 on 2010-03-09
Solved.

I just downloaded an old libexpat file and renamed to libexpat0.so, stuck it into the /star/lib folder, and hey presto - success

---

