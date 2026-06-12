---
title: "Shred folders AND files?"
date: 2011-04-07
forum: General Help
---

### Post by stchman on 2011-04-07
Hello all.

I know that you can do the following:

```

shred -fuzv <file to be shredded>

```

This will completely erase a file off of your HDD.  I have already made this a Nautilus action when right mouse clicking on file(s).

My question is can we do the same thing on a folder with both files and folders under it using a single command?

Thanks.

---

### Post by lithopsian on 2011-04-07
There are a number of utilities to do this in Linux, varying in their scope and brutality.   You might find wipe to be one which fits this need.  I wrap my Thunar custom action with a zenify prompt to avoid costly mistakes ;)

---

### Post by seawolf167 on 2011-04-08
As far as I know you can't use *shred* on directories which is why there is not a --recursive switch (though maybe *wipe* can do that from the previous post)

You could probably shred all the files in a directory tree then remove the folders with rm

Maybe something like

```
find . -type f -execdir shred -fuzv  '{}' ; \
```

then a simple

```
rm -rf *
```

---

