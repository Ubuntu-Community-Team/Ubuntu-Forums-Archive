---
title: "What directory is Mozilla 3.2.6 located?"
date: 2010-04-06
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-04-06
What directory is Mozilla 3.2.6 located?

---

### Post by mickObrian on 2010-04-06
You mean Firefox? Use 'whereis mozilla', it's usually in /usr/bin.

---

### Post by The Real Dave on 2010-04-06
How do you execute it in a terminal? Try

```
which firefox
```

or 

```
which firefox-3.2.6
```

in a terminal [Applications>Accessories>Terminal]

---

### Post by ratcheer on 2010-04-06
On my system, it installed itself in /usr/lib, which seems strange. /usr/bin just has a symbolic link to it in /usr/lib.

I moved it to /opt, which suits me better.

Tim

---

### Post by lovinglinux on 2010-04-06
If you are looking for you personal settings, passwords and such, then is located at ~/.mozilla/firefox.

---

