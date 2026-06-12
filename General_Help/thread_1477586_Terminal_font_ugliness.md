---
title: "Terminal font ugliness"
date: 2010-05-08
forum: General Help
---

### Post by affert on 2010-05-08
I am trying to get my terminal font to not look ugly.  I very recently built a new computer.  My previous computer is a MacBook.  I use Andale Mono 12 point, not AntiAliased for terminal on my Mac.  I strongly dislike the fuzziness that antialiasing gives fonts.  But when I try to use the terminal on Ubuntu with AntiAliasing turned off, it makes the font look boxy and mangled.  I have switched through most of the fonts in the list, and tried different sizes.  All of them look like they're being rendered at a different size, then translated to my resolution.

Is this a setting in Terminal, or something to do with my video card/LCD set up?

---

### Post by chappajar on 2010-05-09
These commands will install Mac fonts on your system: 

wget [http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz](http://ubuntu-debs.googlecode.com/files/macfonts.tar.gz)
tar zxvf macfonts.tar.gz
sudo mv macfonts /usr/share/fonts/
sudo fc-cache -f -v

---

### Post by affert on 2010-05-10
Hmm.   I ran through those instructions.  I now see a few more fonts in my options list, but the fonts still look boxy when I turn Anti-Aliasing off.

Is there something else I'm missing?

Another clue: earlier I'd booted into gnome to share a folder (I haven't learned how to do that from XFCE yet: that'll be a question for another time).  While in gnome, I noticed that the terminal font was the same one I was using in XFCE, and even with AntiAliasing turned off (in gnome) it looked much better.  Is this an unavoidable issue with using XFCE?

---

### Post by chappajar on 2010-05-10
Without anti-aliasing your font edges are simply made up of square pixels, so you should expect them to be boxy.
The only way to get smoother edges without anti-aliasing is to have a higher resolution.  Is your Mac resolution higher?

Andale Mono 12 is silky smooth in my gnome terminal (I assume I have anti-aliasing on -- where/how are you turning it off, BTW?) 

IMHO fonts in Ubuntu versions before 9.10 were always pretty ugly and needed considerable tweaking to look nice, but since 9.10 they've been gorgeous. If you aren't using 9.10 or 10.4 it's time to upgrade...

---

