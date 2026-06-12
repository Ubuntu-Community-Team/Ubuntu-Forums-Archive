---
title: "Bulk rename from context menu..."
date: 2010-03-16
forum: General Help
---

### Post by mrgardon on 2010-03-16
Looking for a rename utility that I can start from the context menu.  Would like to be able to highlight a bunch of dig-cam pix on my desktop, right click to the context menu and open a bunch rename utility.

---

### Post by 2hot6ft2 on 2010-03-16
You might try krename or install it along with krusader to have lots of options when running krusader.
In a terminal
Applications > Accessories > Terminal
you can install them with
```
sudo apt-get install krename krusader
```
Or search for them in synaptic and install them
then they/it will be in Applications > Accessories > KRename or Krusader.

---

### Post by mrgardon on 2010-03-16
Ok, in the proscess of dl'ng both krename & krusader.  Is there an aplication that will allow me to add to or delete items in a context menu?

---

### Post by J V on 2010-03-16
You should learn bash, to rename a bunch of files its easy, but I never learned bash loops, a quick google should do the trick :)

---

### Post by pbrane on 2010-03-16
bash:
```

rename 's/oldname/newname/' *.jpg

```

man rename

---

### Post by mrgardon on 2010-03-16
Appreciate the responses...
and here comes the obligatory 'but...'
I would like to be able to bulk rename a bunch of files that I have dumped on my desk top from my digital cam.  The drill being, select files > click for context menu > click bulk rename, like that.  So what I need is either an application that will get itself into the context menu or a way to put a bulk rename application into the context menu myself.

---

