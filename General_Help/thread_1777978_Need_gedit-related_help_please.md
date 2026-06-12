---
title: "Need gedit-related help please"
date: 2011-06-08
forum: General Help
---

### Post by BaconFTW on 2011-06-08
I've spent most of today writing out a massive chunk of history notes for revision. And now gedit has crashed. Sorta.

[http://k.min.us/iddyP8.png](http://k.min.us/iddyP8.png)

Basically; I can still move the window around, maximize it and minimize it, and the little line that shows where you are in text documents still flickers on and off. I even tried to see if I could open a new document via the terminal and that worked for some reason, as shown in the picture. However, none of the interface responds, and I cannot edit it nor copy anything nor save it. If I click the 'x' button, there is no response, so I can't save it that way.

What do? :(

It would really suck if I have to force quit and lose it.

---

### Post by grahammechanical on 2011-06-08
Did you not save the document as you were working on it? If so, then you will not lose all your work. It could be that the document is too large for Gedit to handle. You may need to delete some of the document before Gedit will allow you to save it. In the past when I was using Windows I found that its text editor was limited as to the size of document that it could handle. This is why I am wondering if you are experiencing a similar issue.

I do not know. I am just guessing. Sorry.

Regards.

---

### Post by seawolf167 on 2011-06-08
I *think *gedit by default creates backup copies of the open files since the last save. If you open a terminal, cd to your working directory and type

```
ls -la
```are there any hidden files by the same name as your notes file? If there are, do any of them contain your [partial] file info? (you could check quick with nano)

```
nano *filename*
```

---

