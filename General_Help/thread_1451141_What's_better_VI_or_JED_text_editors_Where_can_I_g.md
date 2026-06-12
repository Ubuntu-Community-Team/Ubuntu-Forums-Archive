---
title: "What's better VI or JED text editors? Where can I get a tutorial on JED editor?"
date: 2010-04-10
forum: General Help
---

### Post by Young God on 2010-04-10
I have been learning Vim's VI Editor and I also installed the JED Editor onto my system cause I heard it was useful for programmers. My question though is which one is better? should I learn both or just stick with learning one or the other? 

I also need a tutorial on how to use JED editor, I've looked everywhere if someone could please provide a link to a good full-length tutorial with more then just basics (but still including the basics since I know nothing of how to use it, I've been learning the VI editor)?

I also need to know what command I can use to make JED or VI my default editor in my shell/terminal and then what command I can use to switch it back if I need too,

Thanx this forum has been very helpful to me so far.

Young God
Linux User
Web Developer

---

### Post by darolu on 2010-04-10
I have never used JED so I don't have an opinion about it, you can find documentation here though: [http://www.jedsoft.org/jed/docs.html](http://www.jedsoft.org/jed/docs.html)

In the other hand I have used Vim for many years, no one can say a text editor is "the best" or "the better" since it depends on taste and your needs; but I can tell you Vim (VI) is a very mature program, it is really refined and having all this years of developing offers a very robust and stable text editor, is -in my opinion- along emacs the more popular text editors, the advantage is you can find plenty documentation about them.

I've been using gedit lately though, with all the available plug ins it becomes a very powerful tool.

---

### Post by gmargo on 2010-04-10
Which one is better?  That's probably the oldest editor question there is.  The best editor is the one that makes you the most productive, without driving you crazy. Personally, I love Vim.  Some folks like Emacs.  Someone must like Jed too :-)

Tutorial?  I don't know, google's not showing much.

Default editor?  To change the default editor on on a system-wide basis, use the "update-alternatives" command.  That will modify what /usr/bin/editor points to. (See "update-alternatives --list editor" for available installed editors.)  To change the default editor on a personal basis, set the EDITOR environment variable.

---

### Post by motsteve on 2010-04-10
I'm a VI guy myself and am quite surprised an editor flame war hasn't started yet. :)  I haven't tried JED, but I think I read about it on Linuxnow or other pages in the last few days.  I don't think that it is very old.  Try looking on the home web site.

---

