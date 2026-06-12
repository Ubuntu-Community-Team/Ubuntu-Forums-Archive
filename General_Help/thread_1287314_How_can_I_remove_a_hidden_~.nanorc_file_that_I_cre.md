---
title: "How can I remove a hidden ~/.nanorc file that I created?"
date: 2009-10-10
forum: General Help
---

### Post by honey toast on 2009-10-10
Hi, 
I think that I'm getting to like nano, only I'm experiencing a small hang up. I'm trying to set up my nano so that I can have the color syntax highlighting options enabled for my 'c' and 'java' codes. I do not have this set up as of yet. I was reading a blog somewhere that instructed me to create a ~/.nanorc file and then just simply add,
[COLOR=#006600]include "/usr/share/nano/c.nanorc"
include "/usr/share/nano/java.nanorc"

[/COLOR]along with any other mod statement that I want in order to personalize nano. Ummm, eerrrrr...... 
The directory that I created ~/.nanorc does not readily show the ~/.nanorc file. I have to print "ls -a" in terminal in order to see what I presume to be the ~/.nanorc file which manifests itself in the form of "."  -a dot.
I tried it this method to no avail, although, at one point I did see some syntax highlighted when I began to create a piece of java code. But it went away.:(
Any savy nano users out there to assist?

---

### Post by jeremyswalker on 2009-10-10
Umm.. The "." you see in the output of ls -a is not the file you are looking for, it is the current directory. (If I misunderstood what you meant, I apologize). As far as customizing nano goes, I have never looked into it.

---

### Post by mobilediesel on 2009-10-10
> **honey toast said:**
> Hi, 
I think that I'm getting to like nano, only I'm experiencing a small hang up. I'm trying to set up my nano so that I can have the color syntax highlighting options enabled for my 'c' and 'java' codes. I do not have this set up as of yet. I was reading a blog somewhere that instructed me to create a ~/.nanorc file and then just simply add,
[COLOR=#006600]include "/usr/share/nano/c.nanorc"
include "/usr/share/nano/java.nanorc"

[/COLOR]along with any other mod statement that I want in order to personalize nano. Ummm, eerrrrr...... 
The directory that I created ~/.nanorc does not readily show the ~/.nanorc file. I have to print "ls -a" in terminal in order to see what I presume to be the ~/.nanorc file which manifests itself in the form of "."  -a dot.
I tried it this method to no avail, although, at one point I did see some syntax highlighted when I began to create a piece of java code. But it went away.:(
Any savy nano users out there to assist?

I use nano all the time but never used that feature as I didn't know it was there. You don't create a directory called ~/.nanorc just a text file. You'll have to remove the directory then create the file called .nanorc

Here's a list of the syntax coloring files:
```
asm.nanorc  groff.nanorc  java.nanorc  mutt.nanorc    nanorc.nanorc  perl.nanorc  python.nanorc  sh.nanorc
c.nanorc    html.nanorc   man.nanorc   nano-menu.xpm  patch.nanorc   pov.nanorc   ruby.nanorc    tex.nanorc
```

My ~/.nanorc file now looks like this:
```
set nowrap
include "/usr/share/nano/sh.nanorc"
include "/usr/share/nano/patch.nanorc"

```

---

