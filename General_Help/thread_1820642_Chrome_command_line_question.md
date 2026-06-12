---
title: "Chrome command line question"
date: 2011-08-07
forum: General Help
---

### Post by aeronutt on 2011-08-07
I'm trying to change the user directory that chrome uses at startup. The default directory is ~/.config/google-chrome.

Documentation shows that the command line switch "--user-data-dir <dir>" would allow me to select a different directory.

However, all it seems to do is open <dir> in a new instance of chrome, rather than use it as the user data.

Any ideas?

---

### Post by AlphaLexman on 2011-08-08
You are missing an '**equal sign**' between the option and path. Make sure you don't have any whitespace surrounding the '**=**'

Example...
```
google-chrome --user-data-dir[COLOR="Red"]=[/COLOR]/home/username/.my-new-chrome-data-dir
```
Just make sure the directory already exists.

---

### Post by aeronutt on 2011-08-08
OHHH, thank you!  I'll give that a try this evening, makes perfect sense.

---

### Post by aeronutt on 2011-08-08
Ok, that works. But, something else has changed. For example, when I come here to the forums, there's no pull-down menu on the Search, Quick links, etc. (When I start chrome the 'normal' way, all is ok.)

EDIT: never mind, all seems to be worked. Marked as solved. Thanks!

---

