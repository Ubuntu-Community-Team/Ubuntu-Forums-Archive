---
title: "Gimmie"
date: 2010-07-06
forum: General Help
---

### Post by cloroxmartini on 2010-07-06
I've been trying to install Gimmie. So I've gone through a few tutorials and something always seems to go wrong. Right now I run the "make install" command it give me a bunch of error messages. If there is any other bits of information you need to know just ask.

---

### Post by Samulus on 2010-07-06
Those error messages are important ;-) Without them we don't know why it won't install. If you could paste the feedback you get after trying to make install the program we could help you determine why it isn't working. Make sure you paste it in ```
 error message 
``` brackets

---

### Post by cloroxmartini on 2010-07-06
```
Sammy@Duke:~/gimmie-0.2.8$ make install
Making install in data
make[1]: Entering directory `/home/Sammy/gimmie-0.2.8/data'
Making install in images
make[2]: Entering directory `/home/Sammy/gimmie-0.2.8/data/images'
make[3]: Entering directory `/home/Sammy/gimmie-0.2.8/data/images'
make[3]: Nothing to be done for `install-exec-am'.
mkdir -p -- /usr/local/share/icons/hicolor/16x16/apps
mkdir: cannot create directory `/usr/local/share/icons': Permission denied
make[3]: [install-data-local] Error 1 (ignored)
/usr/bin/install -c -m 644 ./gimmie-16.png /usr/local/share/icons/hicolor/16x16/apps/gimmie.png
/usr/bin/install: cannot create regular file `/usr/local/share/icons/hicolor/16x16/apps/gimmie.png': No such file or directory
make[3]: *** [install-data-local] Error 1
make[3]: Leaving directory `/home/Sammy/gimmie-0.2.8/data/images'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/Sammy/gimmie-0.2.8/data/images'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/Sammy/gimmie-0.2.8/data'
make: *** [install-recursive] Error 1

```

---

