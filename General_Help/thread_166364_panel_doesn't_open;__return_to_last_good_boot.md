---
title: "panel doesn't open;  return to last good boot"
date: 2006-04-26
forum: General Help
---

### Post by Hiroshima on 2006-04-26
I had Ubuntu just about configured, I used synapic to install fonts, codecs mplayer, and tux paint.

I Went applications>graphics>tux paint right clicked on tux paint and clicked on "add to panel"  

The panel flickered, some error messages flashed, and went away now whenever I log in, the panel flickers for a while, but then doesn't open.  THe background is there, and so are the two links to the hard drives... but no panel on top or bottom.

How can I get the panel back, or go back to the last good boot?

---

### Post by bswilson on 2006-04-26
Here's what you can do.  From a command line (or non-X interface), navigate to  this location within your home directory:

```
~/.gnome2/panel2.d/default/launchers
```

You'll find multiple files in that directory.  There ought to be one file for each launcher you've added to your panel.  You will need to view each one to determine which one correlates to tux racer.  Use the more command to look at the first several lines, and you should be able to tell.

Once youv'e deleted the file in question, you can restart X Windows (or reboot) and you should be in fine shape.  

Good luck!

---

### Post by Hiroshima on 2006-04-27
to bwilson,

Thanks for the advice, I'm back in Xwindows, and everything worked well!

The one thing I didn't understand was how to restart Xwindows ... I typed startX, but was given a message saying that I was already in .... (which confused me, since I thought I was in a big black screen.  However, that's a different question.  Thanks for getting me back into Ubuntu!

---

### Post by bswilson on 2006-04-28
I'm happy I was able to help you!  Good luck, have fun, and enjoy Ubuntu.  

I've been an AIX, Solaris, and Red Hat user for a long time, and I have to tell you that Ubuntu is easier to manage and a joy to use compared to those other systems!

---

