---
title: "HELP!!! wine window is totally screwed!"
date: 2010-04-20
forum: General Help
---

### Post by hyeeeeeeeeelp on 2010-04-20
Hi, Sorry if this is in the wrong place...


I have had trouble with my wine window. It was scaled too small and i cant reach the controls to scale it back. If i just grab the sides, it just glitches up.

So...Any ideas?
(btw it works on different desktops, but i just want to use my own desktop because it gets a bit annoying when i have to switch user to another desktop just to use wine)

Screenies are here
[IMG]http://www.majhost.com/gallery/111HAHA/klsfnofisdjof/help.jpg[/IMG]
or at least one screenie

---

### Post by hyeeeeeeeeelp on 2010-04-20
I do not want this topic to die. Nor do i want to post it again...


Sorry for this extra post...

---

### Post by 3Miro on 2010-04-20
Have you tried maximize, minimize, resize kwin shortcuts. You might be able to set up geometry under kwin settings somewhere (appearance, desktop effects, or something, I am not sure what).

---

### Post by 3Miro on 2010-04-20
Another ideas is to remove the .wine folder, however, this will destroy all installed windows programs along with at least some of the data that they have.

From Konsole, backup your .wine folder:
```
mv .wine .wine_mybackup
```

Then try wine again

to return to the previous position:
```
mv .wine_mybackup .wine
```

To completely destroy the .wine folder:
```
rm -fr .wine
```

---

### Post by hyeeeeeeeeelp on 2010-04-20
> **3Miro said:**
> Another ideas is to remove the .wine folder, however, this will destroy all installed windows programs along with at least some of the data that they have.

From Konsole, backup your .wine folder:
```
mv .wine .wine_mybackup
```Then try wine again

to return to the previous position:
```
mv .wine_mybackup .wine
```To completely destroy the .wine folder:
```
rm -fr .wine
```

Oh, thanks! that worked!

---

