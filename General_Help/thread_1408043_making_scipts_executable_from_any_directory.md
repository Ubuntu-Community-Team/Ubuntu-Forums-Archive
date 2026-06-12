---
title: "making scipts executable from any directory"
date: 2010-02-15
forum: General Help
---

### Post by stonebergftw on 2010-02-15
Say I have a script called, test.sh, which is located in /home/username/scripts/

I know that I can run it by typing ./test.sh from the /home/username/scripts/ directory... but what do I do to enable the script to be run from anywhere *WITHOUT* having to type the whole directory path?

Thanks in advance.

---

### Post by Richard1979 on 2010-02-15
Make a link to it from /usr/bin/ or just put the script in /usr/bin/.
Or, add /home/username/scripts/ to your $PATH.

---

### Post by stonebergftw on 2010-02-15
Thanks for the quick reply Richard1979.  I knew it was a simple thing.

:popcorn:

---

### Post by ask21900 on 2010-02-15
You can also use an alias entry.  This method does the same exact thing as Richard1979's methods except that using aliases also allows you to hard configure options (change 'du' to 'du -h' automatically), which may or may not be useful to you.

---

