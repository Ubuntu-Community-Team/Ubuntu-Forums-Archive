---
title: "Copying from XTerm"
date: 2009-11-09
forum: General Help
---

### Post by mchilders on 2009-11-09
I'm needing help figuring out how to get ubuntu 9.10 to copy from XTerm to the clipboard when highlighting.  I've found an X resource that I've tried adding several places that doesn't seem to work:
```
XTerm*VT100.translations: #override <Btn1Up>: select-end(PRIMARY, CLIPBOARD, CUT_BUFFER0)
```
I've added a ~/.Xresources file, a ~./Xdefaults file, and added this line to them, as well as added it to my /etc/X11/Xresources file and my /etc/X11/app-defaults/XTerm files (minus the XTerm at the beginning in this file).  I've restarted X and rebooted, I've xrdb -merge with .Xresources and it shows up in a xrdb -query, but I can't get it to copy to clipboard on highlight.

However when I start xterm with the following:
```
xterm -xrm 'XTerm*VT100.translations: #override <Btn1Up>: select-end(PRIMARY, CLIPBOARD, CUT_BUFFER0)
```

It will copy to the clipboard on highlight.  How can I make this a something that happens automatically without having to launch xterm with the -xrm?

Thanks for any help,
Matt

---

### Post by mchilders on 2009-11-09
I'm an idiot... I'm using gnome-terminal not xterm.  xterm works fine, now to figure out how to make it work in gnome-terminal.

---

### Post by b0b138 on 2009-11-09
highlight - right click - copy

---

### Post by aaronharder on 2011-04-23
> **b0b138 said:**
> highlight - right click - copy

Yeah, except that sucks.  What many users actually want is, on select, for Gnome Terminal to copy to the ***primary*** clipboard.  Copying to the secondary clipboard ends up not being useful for me 99% of the time (for example when you don't have a middle mouse button handy and/or when you are moving a URL from the shell to a browser).  The most popular terminals under Mac and Windows copy-on-select to the primary clipboard (admittedly on those systems, that's the only clipboard) out of the box and/or can be configured to do so easily.  It is a real mystery to me why under Linux it is so difficult to do.  Perversely, this hiccup makes the shell experience under Mac and Windows ***much better*** than the shell experience under Linux.  :(   For me it does, anyway.  And I'm guessing I'm not alone.

---

### Post by Vaphell on 2011-04-23
windows doesn't allow you to highlight-paste at all (and it's painful every time i am reminded of that fact when I use windows:))

can't you use ctrl+shift+c in terminal (as ctrl+c is used to kill programs there), ctrl+v (ctrl+shift+v in terminal)?

---

