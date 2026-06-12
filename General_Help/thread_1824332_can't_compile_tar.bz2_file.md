---
title: "can't compile tar.bz2 file"
date: 2011-08-13
forum: General Help
---

### Post by princeofnam on 2011-08-13
I need to downgrade my firefox from 5 to 3.6  I downloade the tar.bz2 file but after I extracted and cd to the file I got these errors when trying to install

"x@y:~/Downloads/firefox$ ./configure
bash: ./configure: No such file or directory
x@y:~/Downloads/firefox$ make
make: *** No targets specified and no makefile found.  Stop.
x@y:~/Downloads/firefox$ 

"

---

### Post by GWBouge on 2011-08-13
If you got it from _[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)_, it doesn't look like you have to compile it, just run the firefox executable

```
$ cd ~/Downloads/firefox
$ ./firefox
```

---

