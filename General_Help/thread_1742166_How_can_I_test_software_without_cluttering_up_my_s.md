---
title: "How can I test software without cluttering up my system?"
date: 2011-04-28
forum: General Help
---

### Post by sparrowkc on 2011-04-28
I was recently playing with building some things from source, and to do that I had to install all kinds of libraries, including lots of components of KDE.  I'm done compiling, but now I have all this software installed that I'll never use again.  I'm about to do a fresh install of 11.04; is there a way I could maintain a test environment of some kind so that this doesn't happen in the future?  I'm just guessing that people have come up with a way to deal with this problem.

---

### Post by Lolpanda on 2011-04-28
For the compiled software itself you could install it to 

/opt/

or make a "bin" folder in your HOME folder. For actually going back through and removing the libraries, Synaptic (if you used it) has a log file of everything installed on a per-day basis, so you could go through the log file and just mark them all for removal.

Beyond THAT... Virtual box is all I can think of but thats a whole new install

---

