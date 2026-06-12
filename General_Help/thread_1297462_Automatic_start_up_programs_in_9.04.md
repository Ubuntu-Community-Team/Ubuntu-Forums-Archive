---
title: "Automatic start up programs in 9.04"
date: 2009-10-21
forum: General Help
---

### Post by darms21 on 2009-10-21
How can I go tell Firefox 3.5 (Shiretoko) to automatically starting when I log onto my account.

---

### Post by skatinjj on 2009-10-21
system > preferences > startup applications

---

### Post by darms21 on 2009-10-21
I tried that and when I added firefox out of the /etc file an editor loaded with text, not the browser

---

### Post by itsjareds on 2009-10-21
For the command to start up, either put:
```
firefox
```

or:
```
/usr/bin/firefox
```

---

### Post by darms21 on 2009-10-21
Thank you guys very much, got it. Much appreciated. Keep it up Ubuntu forum.

---

### Post by Earl_Maroon on 2009-10-21
System>Preferences>Startup Applications

I think you just need to add an entry for Firefox with the command "firefox".

I'll also add that you can easily install the latest official Mozilla build of Firefox (with full branding etc.) using Ubuntuzilla.py, downloadable from [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) .

---

### Post by itsjareds on 2009-10-21
The latest official FF3.5 build comes by default in Ubuntu karmic in almost 7 days when it is released.

---

