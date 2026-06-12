---
title: "CLI based - mini install - application for opening word documents"
date: 2010-12-03
forum: General Help
---

### Post by e24ohm on 2010-12-03
Folks:
I am looking for an cli based application what will open microsoft office documents in a cli based window. Very similar to the old Word for DOS application.

Not I will be running this on the mini install, so no gui or packages are avalible.

Can anyone offer any suggestions?

---

### Post by wojox on 2010-12-03
Try

```
sudo apt-get install catdoc
```

```
catdoc filename.doc
```

```
catdoc filename.doc > /tmp/output.txt
```

---

### Post by e24ohm on 2010-12-03
> **wojox said:**
> Try

```
sudo apt-get install catdoc
```

```
catdoc filename.doc
```

```
catdoc filename.doc > /tmp/output.txt
```

That might be a solution and i will try it; however, I was looking for something that has a tool bar with options, similar to nano, but with more extensive capabilities somewhat more along the lines of Vi; however, I need the capability to manage word documents and opendocument formats.

thanks

---

### Post by I'mGeorge on 2010-12-03
how about this [http://www.linux.com/archive/feed/52385](http://www.linux.com/archive/feed/52385) By the way I use nano instead of vi as a CLI text editor, I find it far more easy to use.

---

### Post by e24ohm on 2010-12-03
> **I'mGeorge said:**
> how about this [http://www.linux.com/archive/feed/52385](http://www.linux.com/archive/feed/52385) By the way I use nano instead of vi as a CLI text editor, I find it far more easy to use.

I couldn't agree more with you about Nano; however, I do like the cut/paste function of Vi, which comes in handy at times.

thanks - I'll give the article a read.

---

### Post by SlugSlug on 2010-12-03
not tried it yet, but emacs gets highly spoken of

---

