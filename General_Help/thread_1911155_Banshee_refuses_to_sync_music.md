---
title: "Banshee refuses to sync music"
date: 2012-01-18
forum: General Help
---

### Post by bobman321123 on 2012-01-18
Banshee will convert the music, and then apparently add it to my ipod, but nothing will happen.
I have banshee 2.2.1
My ipod is an ipod touch 2G 32gb firmware version 4.2.1 which has been jail broken with green poin0n. 
Gah, this is irritating me.
Any ideas?

---

### Post by dino99 on 2012-01-18
your logs might help you to know about warnings/errors:
- .xsession-errors into /home
- /var/log/

---

### Post by bobman321123 on 2012-01-21
When I ran:

```
.xsession-errors into /home
```
it returned

```
.xsession-errors: command not found
```

---

### Post by raja.genupula on 2012-01-21
Its not a command.
what dyno99 was trying to say is
.xsession-errors is a hidden file in your home directory

&

/var/log/ this is the place of your system logs.
var is a directory in your filesystem.

---

