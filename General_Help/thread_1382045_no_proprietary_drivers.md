---
title: "no proprietary drivers"
date: 2010-01-15
forum: General Help
---

### Post by MarcusA on 2010-01-15
Hi

I just reinstalled Karmic Koala on my system and I went to hardware drivers.. However there it says "no proprietary drivers are in use on this system" It doesnt give me any option to click on :( In earlier versions I had about 3  options or so to choose from but now nothing? anything i can do about this?

thanx

This is what it looks like btw:

  [IMG]http://i45.tinypic.com/2wlt5jb.jpg[/IMG]

---

### Post by howefield on 2010-01-15
Open a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Enter your password when prompted and try the hardware drivers again.

---

### Post by jward3010 on 2010-01-15
What hardware do you need proprietary drivers for? It's usually for wireless or graphics cards.

There's a possiblilty that a that particular driver you used in the past has been discontinued for Karmic, maybe because of stability.

---

### Post by MarcusA on 2010-01-15
> **howefield said:**
> Open a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```Enter your password when prompted and try the hardware drivers again.
](*,) I can't believe I didn't think of updating first, thanx mate.

---

### Post by howefield on 2010-01-15
> **MarcusA said:**
> ](*,) I can't believe I didn't think of updating first, thanx mate.

You're welcome, we've all been there. ;)

---

