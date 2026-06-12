---
title: "How to use softwares downloaded from the Synaptic Package manager?"
date: 2009-12-06
forum: General Help
---

### Post by linux_dream on 2009-12-06
I've downloaded a lot of programs via the Synaptic Package Manager, but I've no idea about how to use them.
For example I've downloaded gfortran, polyglot (for chess) and a lot more.  But I'm totally unable to use them.  
I'm new to Ubuntu/linux.  I only know how to use softwares I download from Ubuntu Software Center because they appear in the Application list.
Thank you in advance!

---

### Post by nothingspecial on 2009-12-06
Applications that do not appear in your menus tend to be command line applications. For information on how to use them open a terminal and type ```
man *packagename*
```

so 

```
man gfortran
```
```
man polyglot
```

---

### Post by linux_dream on 2009-12-06
Ah, thank you so much!
Last thing: in order to use polyglot, it says to type " xboard -fd 'polyglot_dir' -fcp 'polyglot engine.ini".

But I don't know how to search the directory of polyglot nor any other software.  What should I type?

---

### Post by nothingspecial on 2009-12-06
What are you actually trying to do?

If you are trying to code a chess game or link polyglot to an existing chess game then you need to ask in a more advanced forum, maybe the Ubuntu programming forum.

If you just want to play chess, you are trying to run the wrong application.

---

### Post by linux_dream on 2009-12-06
I just want to play chess.  I've downloaded 2 chess engines (fruit and crafty).

---

### Post by nothingspecial on 2009-12-06
Then use a chess game rather than an engine.

---

### Post by linux_dream on 2009-12-06
> **nothingspecial said:**
> Then use a chess game rather than an engine.
What do you mean by a chess game?  
I've typed "xboard -fcp fruit -fUCI"and I could play against Fruit.  However I find Xboard very different from Winboard.  But I'm ok with it.

Thank you very much for all your help.

---

### Post by nothingspecial on 2009-12-06
> **linux_dream said:**
> 

Thank you very much for all your help.

That`s no problem atall. :D

However, I don`t play chess. So I don`t know what I`m talking about. It seemed to me, from looking at the polyglot man page (hint - all man pages are on the internet, you can type man polyglot into google aswell), that polyglot is a program that makes your chess game behave in a specific way.

> polyglot - is a chess engine protocol adaptor. It connects a UCI protocol engine to xboard frontend.

I know knothing of connecting UCI protocol engines to xboard frontends.

Perhaps someone in the [[COLOR="Magenta"]Ubuntu gaming & leisure[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=93") forum does.

You are probablly better asking there.

Hope you get it sorted.

---

### Post by linux_dream on 2009-12-06
Ok thank you once again.
I've reached what I wanted : to be able to play against UCI engines.  
Some engines like GNUchess aren't UCI type of engine, so I don't need polyglot to run them on xboard.  Other engines (such as Fruit and the most recent ones) are UCI types of engine (although I don't really know what it is) and I need polyglot to run them.  I've succeeded in it.  I'm done :).

---

