---
title: "Dapper Search"
date: 2006-05-04
forum: General Help
---

### Post by thunderduck3141 on 2006-05-04
Hi evrybody,
I have a problem with the file search program included with Dapper Beta, it can't find anything, or hardly anything, i was wondering if this is my fault (probably is) or if it is a bug in the program
If u need a technical printout I would be glad to provide one
Thanks

---

### Post by Qrk on 2006-05-04
Beagle or the Gnome search?

Gnome's find tool uses locate/find commands. It is purely a GUI attached to them.


So you probably have a problem with Beagle. (is Beagle on the Dapper cd or just in the repositories?) 

Beagle has to index your data before you can use it. Most likely it hasn't finished indexing the data yet. You can have it quickly index stuff with this command:

```
export BEAGLE_EXERCISE_THE_DOG=1
```

And for a guide, check here:

[http://beaglewiki.org/Indexing_Data](http://beaglewiki.org/Indexing_Data)

---

### Post by thunderduck3141 on 2006-05-06
thank you, that worked just fine
this is one of the main reason i LOVE Ubuntu, its community support

---

