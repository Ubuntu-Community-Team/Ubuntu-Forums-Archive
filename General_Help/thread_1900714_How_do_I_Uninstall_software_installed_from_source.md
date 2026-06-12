---
title: "How do I Uninstall software installed from source?"
date: 2011-12-27
forum: General Help
---

### Post by QuickSphinx on 2011-12-27
I know that if there was a rule for uninstall for the makefile I could just make uninstall. But there isn't in mine


Where does the software go? How Do I uninstall/remove this software? the install log only tells me:

```
./miniruby -I./lib -I.ext/common -I./- -r./ext/purelib.rb  ./instruby.rb --make="make" --dest-dir="" --extout=".ext" --mflags="" --make-flags="" --data-mode=0644 --prog-mode=0755 --installed-list .installed.list --mantype="doc"
installing binary commands
installing command scripts
installing library scripts
installing headers
installing manpages
installing extension objects
installing extension scripts
```

---

### Post by raja.genupula on 2011-12-27
You can remove it from synaptic i think.... where all the install pkg's with library's  going to exist . make a look at there . 

and try this if above one wont work 

sudo apt-get remove <here place the name by which you will invoke your app from terminal >

---

### Post by QuickSphinx on 2011-12-27
Thanks

---

