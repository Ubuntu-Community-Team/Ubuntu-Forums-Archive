---
title: "Can I automatically change the case of filenames?"
date: 2010-11-08
forum: General Help
---

### Post by ninjaaron on 2010-11-08
I have a directory with almost 4000 files, and all of their titles are in upper-case. The program I'm using needs them to be in lower-case. Doing by hand would take a while, and be error prone, methinks.

---

### Post by sanderj on 2010-11-08
[http://www.linuxjournal.com/content/convert-filenames-lowercase](http://www.linuxjournal.com/content/convert-filenames-lowercase)

---

### Post by ninjaaron on 2010-11-08
Looks like what I need. How do I use it? just copy the stuff into a text file, save it with *.sh, go to the directory in a terminal, and run the script there?

I've never built a script... I'm not even sure if I've used one from the command line before.

---

### Post by nothingspecial on 2010-11-08
Go to the directory with the files in a terminal, type

```
rename -n 'y/A-Z/a-z/' *
```

The -n option will just show you what would happen if you ran that command.

If the results are correct, run it again without the -n

---

### Post by ninjaaron on 2010-11-08
Ok, got the script running and all is well. Thanks!

---

