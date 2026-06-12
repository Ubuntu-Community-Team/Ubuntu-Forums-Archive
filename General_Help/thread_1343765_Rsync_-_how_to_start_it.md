---
title: "Rsync - how to start it ?"
date: 2009-12-02
forum: General Help
---

### Post by mikeody on 2009-12-02
I want to have a look at rsync - what it can do etc etc.
A silly question I know, but it is installed in my Karmic but how do I run it ?
Its not in any of the application menus and doesnt respond to sudo rsync.
There must be an answer for thick people like me - help !!

---

### Post by memilanuk on 2009-12-02
Try 'man rsync', which should pull up the 'man'ual page for the command, if it is installed.  If it is not, then try 'sudo apt-get install rsync' to install it.  The command is usually followed by a string of 'flags' basically a '-' and various characters' that tell the command what options you want to use, and then the name of the files you want it to work with.  Just using the command 'rsync' by itself won't do much if anything  besides gripe about the lack of information passed to it.  

Here is a link to some docs on the command that show the potential uses (and are a little bit less terse than a man page):

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

FWIW, I would highly recommend playing with rsync as a regular user inside your home directory (or even a 'test' directory inside that as a sort of sandbox) before trying to run it via 'sudo'.  That way if you screw up, you don't nuke portions of your file system!

HTH,

Monte

---

### Post by mikeody on 2009-12-03
Thanks Monte - just what I needed.

---

