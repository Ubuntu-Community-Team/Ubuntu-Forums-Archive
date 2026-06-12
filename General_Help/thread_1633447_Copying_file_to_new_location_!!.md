---
title: "Copying file to new location !!"
date: 2010-11-29
forum: General Help
---

### Post by Tom_T on 2010-11-29
Hi
I need some advise on this..

file is named similar to : logout 10.10.10 100817.txt

I need to copy this to a new directory.

To fine the latest file I was advised to use:
```
ls -tr logout* | tail -n 1
```
This works.  

Then I was advised to use this to copy it:
```
cp `ls -tr logout* | tail -n 1` anonymous/
```
But this returns:```

cp: logout: No such file or directory
cp: 10.10.10: No such file or directory
cp: 100817.txt: No such file or directory
```

So my question is HOW do I do this ?
Thanks :)

---

### Post by cicatrix1 on 2010-11-29
This should work (because the cp argument is in quotes, which makes bash treat it as a single filename).  It's also good to avoid spaces in your file names (replace with '_') if you can help it.

cp "$(ls -tr logout* | tail -n 1)" anonymous/

---

### Post by Tom_T on 2010-11-29
Thanks

This just returns:

```
cp: ls -tr logout* | tail -n 1): No such file or directory
```

```
(ls -tr Backup* | tail -n 1)
``` by itself returns the correct file !!

Any ideas ?

---

### Post by Tom_T on 2010-11-30
Can anyone help me with this ?

---

