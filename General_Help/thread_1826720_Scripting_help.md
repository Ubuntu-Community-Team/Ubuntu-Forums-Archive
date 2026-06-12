---
title: "Scripting help"
date: 2011-08-17
forum: General Help
---

### Post by Weidbrewer on 2011-08-17
Hey all - I've taken a stab at creating a script, and by all accounts it works.  There is just one minor thing that I was hoping that I could smooth out with it.  Let me stress:  this is *minor* and if can't be done, I'm cool with that.

I have the Calibre ebook software on my wife's computer, and the way it updates is with a binary command that just pulls the software down and reinstalls it (updates are frequent, and the repos version is always way behind.)  As she is not comfortable with the command line, I created this script and a menu-launcher to run it in terminal.  This script is simply:

```
#!/bin/bash
sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"

```

Simple.  The one and only thing is that when it runs (in terminal) it asks you to confirm the install directory and you hit enter.  Then, it downloads, installs and closes terminal.  

What I would *love* is if there is something I can add to the script to have it handle hitting 'enter' as well, so that the end result is that my wife clicks the launcher, and it handles everything else.

Can this be done?  (Again, I realize that this is stupidly minor, but it bugs me.)

---

