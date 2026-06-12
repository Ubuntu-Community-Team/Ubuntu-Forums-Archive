---
title: "mknod /dev/null"
date: 2010-06-23
forum: General Help
---

### Post by ctult on 2010-06-23
When I ran /dev/null, it only let me send about 392 MB and then it said "System out of memory." or something like that.  So I looked it up and found how to fix it.  I (stupidly) tried it, and it worked, but I would like to know what is going on.

```

#Run under root.
rm -f /dev/null
mknod /dev/null c 1 3
chmod a+w /dev/null

```

Also, I can't seem to find anything about mknod.  I searched for hours.

EDIT:  I know what rm and chmod are doing, just not mknod.

---

### Post by bodhi.zazen on 2010-06-23
What is it you want to know exactly ?

[http://linux.die.net/man/2/mknod](http://linux.die.net/man/2/mknod)

[http://www.adamsinfo.com/mknod-tutorial/](http://www.adamsinfo.com/mknod-tutorial/)

[http://linux.about.com/od/lsa_guide/a/gdelsa23t01.htm](http://linux.about.com/od/lsa_guide/a/gdelsa23t01.htm)

---

