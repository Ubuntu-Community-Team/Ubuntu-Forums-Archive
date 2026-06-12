---
title: "Images not showing on a website."
date: 2009-07-17
forum: General Help
---

### Post by Fatguyinspandex on 2009-07-17
For some reason about 3 weeks ago [www.ziprealty.com](www.ziprealty.com) stopped displaying pictures. at first i thought it was the site. but i checked on my moms pc and it works fine. every other site I have been to loads up fine. everything shows up. its just this one site. anyone have any idea how to fix it?

using 8.10 64bit

---

### Post by nikhilk on 2009-07-17
Which browser are you using? Can you try visiting that site through some other browser and see if it displays images?
Try to isolate the problem which most likely seems to be with the browser.

---

### Post by Fatguyinspandex on 2009-07-17
I am running FF 3.0.11. I just installed opera and it works on there. but opera seems to be a bit slow..

wlso with firefox whenever i  minimize it and bring it back up it comes back in in fullscreen(f11) which is annoying.

---

### Post by vinutux on 2009-07-17
Try from another user or if you are don't mind delete /hom/yourusername/.mozill folder (you are going to lost every bookmarks and extension installed after fresh ubuntu)

```
rm /home/yourusername/.mozilla
```

.

---

### Post by nikhilk on 2009-07-17
> **vinutux said:**
> Try from another user or if you are don't mind delete /hom/yourusername/.mozill folder (you are going to lost every bookmarks and extension installed after fresh ubuntu)

```
rm /home/yourusername/.mozilla
```

Alternatively, just backup your current Firefox profile directory (quit Firefox before doing this)
```
mv /home/<username>/.mozilla/firefox
```
and then fire up Firefox and see if the problem is resolved.

---

### Post by Fatguyinspandex on 2009-07-17
> **nikhilk said:**
> Alternatively, just backup your current Firefox profile directory (quit Firefox before doing this)
```
mv /home/<username>/.mozilla/firefox
```
and then fire up Firefox and see if the problem is resolved.

Still not working. And it is actually starting up in fullscreen too... anooying. and ziprealty still does not show up. at this point its not really a big deal. I can just fire up opera and use that when i want to look on the site. and the fullscreen issue while annoying is just a few clicks of f11.

---

### Post by nikhilk on 2009-07-17
Mea culpa, the mv command in my last post was incomplete, should have been```
mv /home/<username>/.mozilla/firefox /home/<username>/.mozilla/firefox_bak
```
I hope you got that right though.

Ok, one last try. Purge the firefox package from Synaptic and then install it again.

---

