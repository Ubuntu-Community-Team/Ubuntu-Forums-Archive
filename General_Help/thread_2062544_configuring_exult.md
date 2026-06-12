---
title: "configuring exult"
date: 2012-09-25
forum: General Help
---

### Post by arnicainthemembrane on 2012-09-25
Hi, I'm trying to configure exult, adding program files to the ultima game engine. I'm told to look for a cfg file, but what I found in usr/share/games/exult is:

exult_bg.flx  exultmsg.txt  midisfx.flx          u7siintrinsics.data
exult.flx     exult_si.flx  u7bgintrinsics.data

which of these files do I configure? Any tips? Thanks.

---

### Post by Wim Sturkenboom on 2012-09-25
Does this help? [http://exult.sourceforge.net/faq.php#where_cfg](http://exult.sourceforge.net/faq.php#where_cfg) , point 3.2, $HOME indicates the user's home directory

---

### Post by arnicainthemembrane on 2012-09-25
yeah but there isn't a .cfg file.

---

### Post by Wim Sturkenboom on 2012-09-25
You are aware that the file is hidden (as it starts with a dot)?

---

### Post by arnicainthemembrane on 2012-09-27
how do you access hidden files using only the CLI?

---

### Post by Wim Sturkenboom on 2012-09-27
```

ls -al

```
executed in your home directory will show the file

you can edit it as you would do with any file

```

YourFavoriteEditor .exult.cfg

```
e.g. (assuming you're in your home directory)
```

vi .exult.cfg

```

---

### Post by arnicainthemembrane on 2012-09-28
oh, there is is! thanks. now to figure out how to configure it..

---

