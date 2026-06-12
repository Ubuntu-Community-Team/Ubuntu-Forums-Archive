---
title: "I STILL have no sound -_-"
date: 2010-02-09
forum: General Help
---

### Post by THE GMoD on 2010-02-09
Well it has been a month and I am still battling against my soundless problem, I have no sound in Gnome, KDE, or XCFE...
and its really pissing me off!!!

OK for starts...
[[IMG]http://img59.imageshack.us/img59/6183/screenshotbk.png[/IMG]](http://img59.imageshack.us/i/screenshotbk.png/)
[[IMG]http://img32.imageshack.us/img32/4396/screenshottl.png[/IMG]](http://img32.imageshack.us/i/screenshottl.png/)
[[img]http://www.betaarchive.co.uk/imageupload/1265749551.th.674987.jpg[/img]](http://www.betaarchive.co.uk/imageupload/1265749551.or.674987.png)
[[img]http://www.betaarchive.co.uk/imageupload/1265749748.th.796933.jpg[/img]](http://www.betaarchive.co.uk/imageupload/1265749748.or.796933.png)
what did I do wrong????

---

### Post by Barriehie on 2010-02-09
I too have the same card and went round and round...  Try this:
```

modprobe snd-**drive partition**-**CA0106**
```

It would/might look like this: (depending on your kernel drive)
```

modprobe snd-sda1-CA0106
```
Barrie

---

### Post by THE GMoD on 2010-02-09
> **Barriehie said:**
> I too have the same card and went round and round...  Try this:
```

modprobe snd-**drive partition**-**CA0106**
```

It would/might look like this: (depending on your kernel drive)
```

modprobe snd-sda1-CA0106
```
Barrie
sadly no....

---

### Post by Vaphell on 2010-02-09
command line alsamixer doesn't have anything muted by defalt?

---

