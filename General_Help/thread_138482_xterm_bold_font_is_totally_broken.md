---
title: "xterm bold font is totally broken"
date: 2006-03-02
forum: General Help
---

### Post by stiaszny on 2006-03-02
I installed a box a few months ago from the 5.10 boot image.  Other than the xterm scrollbar issue, everything worked fine.

I installed a box today from the same boot image, and the bold font in xterm is totally broken (whereby I mean it renders unacceptibly, to the point of being illegible), and the colors are wrong.  What is the deal here, and how do I fix it?  Most importantly, what changed?  My old, old debian install had the wrong colors problem, and the colors seem to be the same as that situation.

I came to ubuntu because I had heard of their moto about things should just work, and I must say, this is very disappointing.  

How do I determine what font xterm is using?

---

### Post by lennox on 2006-03-21
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=318162](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=318162))

the workaround is also found there:
Disable boldMode in .Xresources ("XTerm*boldMode: false").

---

### Post by casperlingus on 2006-04-18
And where exactly *is* .Xresources?  I don't have it in my home directory, and creating one doesn't seem to do anything.  I did an slocate for it and found an Xresources directory which has xorg-common and xbase-clients in it, but that's it.  

This is really frustrating because I use fluxbox on my laptop which relies on xterm and I tend to do all my programming on my desktop in vim in an xterm -- I am *really* displeased with xterm colors breaking like this.  Please please please fix this in Dapper.

Casper...

---

### Post by casperlingus on 2006-04-18
Okay, I finally found a solution to this problem, I'm am posting for reference to anyone else who might have been frustrated by this.  I noticed that modifying /etc/X11/app-defaults/XTerm-color did nothing... unless you explicity call xterm with a -class argument.

The top of my XTerm-color looks like the following:



```
! $XTermId: XTerm-col.ad,v 1.17 2005/07/07 00:46:13 tom Exp $
! $XFree86: xc/programs/xterm/XTerm-col.ad,v 3.6 2005/07/07 00:46:13 dickey Exp $

#include "XTerm"

*VT100*colorMode: on
*VT100*boldMode: false
*VT100*dynamicColors: on
*VT100*foreground: white
*VT100*background: black
```

After that when you want to run an xterm you type:

```
xterm -class XTerm-color
```

I just added a custom button to the top panel and used that line for the command.  All is well now.

Casper...

---

