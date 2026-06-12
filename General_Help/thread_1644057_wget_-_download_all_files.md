---
title: "wget - download all files"
date: 2010-12-12
forum: General Help
---

### Post by nothingspecial on 2010-12-12
I go here

[http://ia700302.us.archive.org/10/items/gd89-07-04.aud.wiley.9045.sbeok.shnf/](http://ia700302.us.archive.org/10/items/gd89-07-04.aud.wiley.9045.sbeok.shnf/)

which is a legal place for downloading music.

I try
```

wget -A.shn http://ia700302.us.archive.org/10/items/gd89-07-04.aud.wiley.9045.sbeok.shnf/
```It doesn`t work.

I can download the files individually.

What am I doing wrong?

Thanks.

---

### Post by AlphaLexman on 2010-12-12
I am not a 'wget' expert, but shouldn't you have some whitespace after the option '-A'?

---

### Post by TiBaal89 on 2010-12-12
I've done this before, but can't get it to work either... I'm trying:

```
wget -nd -r -l1 -A.shn <URL>
```

which makes it "recursive" but only at depth one (i.e. this folder only).  Not sure why that isn't working... hmmm

---

### Post by nothingspecial on 2010-12-12
> **AlphaLexman said:**
> I am not a 'wget' expert, but shouldn't you have some whitespace after the option '-A'?

I thought so at first but apparently not.

---

### Post by tekkidd on 2010-12-12
Well one problem i see is you have it pointed to the directory instead of the individual file try somthing like this 
```
wget http://ia700302.us.archive.org/10/items/gd89-07-04.aud.wiley.9045.sbeok.shnf/gd89-07-04d1t01.ogg
```

---

### Post by TiBaal89 on 2010-12-12
Yea I just went ahead and ran exactly the command I suggested on a different website and it worked... something strange is afoot.

---

