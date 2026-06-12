---
title: "Permission problem with fonts"
date: 2009-07-24
forum: General Help
---

### Post by ibexslam on 2009-07-24
I've been trying to install some .ttf font files on my wubi'd jackalope.  New fonts that I slip into my home/.fonts folder don't seem to have permission, which - I'm guessing - is the reason they're not showing up in any applications.  I tried to sudo chmod the files, but there seems to be no change in the permissions...don't know why.

Any ideas?

I.

---

### Post by Finalfantasykid on 2009-07-24
try going...

```
sudo nautilus
```and then putting the files in there now.

EDIT:  Actually what you probably want to do is put them in this folder /usr/share/fonts

---

### Post by ibexslam on 2009-07-24
That sudo nautilus is a handy can opener.  I was able to change the permissions easily.

And yet, my new fonts aren't showing up after a restart.

I'll try that other folder and see how that works out.

---

### Post by ibexslam on 2009-07-24
/usr/share/fonts is the place to be if you're a font, evidently.  That makes it work.  Thank you.

I.

---

### Post by Finalfantasykid on 2009-07-24
Glad I could help :)

I had the same problem in the past, and when I searched it on google, I came up with results saying to try what you did (in the .fonts folder), but that didn't work.  Maybe thats where they would go in older versions or something...

---

