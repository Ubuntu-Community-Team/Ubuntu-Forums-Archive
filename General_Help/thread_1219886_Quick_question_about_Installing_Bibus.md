---
title: "Quick question about Installing Bibus?"
date: 2009-07-22
forum: General Help
---

### Post by oxf on 2009-07-22
The instructions for installing Bibus
[http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu)
state that you should add the following lines in the Software sources list

"deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./"

Do I add them in the "Third Party Software Tab"?

And since under "Add" the "APT Line" only allows one line do I add them above one after the other?

Thanks for the advice!

---

### Post by Psycho.mario on 2009-07-22
Either put them in, one at a time, into the third party tab, OR, run:
```
sudo gedit /etc/apt/sources.list
```
and paste those two lines on the end.

---

### Post by oxf on 2009-07-22
> **Psycho.mario said:**
> Either put them in, one at a time, into the third party tab, OR, run:
```
sudo gedit /etc/apt/sources.list
```and paste those two lines on the end.

OK great...Thanks!:)

---

