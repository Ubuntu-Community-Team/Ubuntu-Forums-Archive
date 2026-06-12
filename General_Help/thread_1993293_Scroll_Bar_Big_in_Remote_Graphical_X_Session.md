---
title: "Scroll Bar Big in Remote Graphical X Session"
date: 2012-06-01
forum: General Help
---

### Post by Joshua on 2012-06-01
I'm having a problem scrolling when I try to use a program remotely via SSH.  Here's what happens.

I have a desktop downstairs with Ubuntu 11.10.  I have a netbook upstairs with Windows XP and Cygwin/Xserver installed.  I like to interface with graphical programs on the desktop from the netbook via SSH.  I run:

```
$ssh -X user@server
```

to log in.  Then I run the program I want from the command line and it just pops up on my little netbook.  Unfortunately, some programs don't show scroll bars.  I think it started happening after Ubuntu switched to using those skinny scroll bars where the arrows only show up after you hover the mouse over the bar.  Some programs work, but most don't.  For example, gedit looks like it has skinny bars but I can't grab them to scroll up or down.  Gnu-cash has normal bars.

Anyone know how to fix this?  Or where a bug report should be sent?

---

