---
title: "Ubuntu application on windows"
date: 2010-01-29
forum: General Help
---

### Post by hawthornso23 on 2010-01-29
My parents (late 80s) came around for a visit yesterday and my mother (who loves puzzles) fell in love with some of the ubuntu puzzle type games I have installed. I'd like to send her one game (pattern) via email and was wondering if there is an easy way to package up a single small application so that a windows user can run it without installing all the rest of ubuntu. Kind of a wubi wrapper for one application only. I don't want to try to switch them to ubuntu. It is a big ask for someone that old to consider switching operating systems and probably isn't worth it just to get one or two games running.

Does something like what I am imagining exist?

---

### Post by AndyM3 on 2010-01-29
Can you give the game's package name? (you can probably find the package name using Synaptic)
There might be a Windows version of it. If not, it might be possible to recompile it using Cygwin or run it in a VM.

---

### Post by hawthornso23 on 2010-01-29
The package name in synaptic is  sgt-puzzles

It has a bunch of puzzle type games including the particular one I'm after.

---

### Post by hawthornso23 on 2010-01-29
... and indeed that solved it. Running a google search on the package name gives

[http://www.chiark.greenend.org.uk/~sgtatham/puzzles/](http://www.chiark.greenend.org.uk/~sgtatham/puzzles/)

and indeed there are windows versions. Thanks for the hint. I didn't know what to search for.

---

### Post by AndyM3 on 2010-01-29
Glad I helped :D

---

### Post by SecretCode on 2010-01-29
And in fact, that puzzle collection was **written** to be portable between operating systems!
> Simon Tatham's Portable Puzzle Collection
...
All of them run natively on Unix (GTK), on Windows, and on Mac OS X; they can also be played on the web, as Java applets.

I wrote this collection because I thought there should be more small desktop toys available: little games you can pop up in a window and play for two or three minutes while you take a break from whatever else you were doing. And I was also annoyed that every time I found a good game on (say) Unix, it wasn't available the next time I was sitting at a Windows machine, or vice versa; so I arranged that everything in my personal puzzle collection will happily run on both those platforms and more.

For applications that don't have a native Windows version, you would need to look at something like [cygwin]("http://www.cygwin.com/").

---

