---
title: "Panelbar and launcher broken!"
date: 2011-09-11
forum: General Help
---

### Post by aP0THE0Sis on 2011-09-11
Hi,

I am completely new to linux, this is my second day after installing ubuntu 11.04.
I was playing around with the settings in compiz yesterday,

today, i noticed that the panelbars look really weird.  Here is a picture
[IMG]http://img16.imageshack.us/img16/3894/workspace1002.png[/IMG]


I noticed that if i set the opacity of unity to 100 the top panelbar looks normal but if i decrease it at all, it looks "fuzzy" like in the picture above.

The loader bar on the left is hidden and thats what it looks like after it hides.  when it pops up, it looks the same with icons over it.

What did I do to break it??

---

### Post by MG&amp;TL on 2011-09-11
Have you tweaked anything else in ccsm? Some things, like the cube, and some of the other effects, don't work on Unity yet. I get this, for instance, when I enable wobbly windows. But not everybody does, it seems to be a hardware thing.

---

### Post by harlequin_ on 2011-09-11
Hi and welcome to the forums,

Can you please open a terminal (click on the ubuntu icon at the top left of the screen, type "terminal" and press enter) and then type in it

```
unity --reset
```

and then press enter? This will reset the unity to its default configuration (so if you made changes on the unity they will be reset). 

Does this improve the situation?

---

### Post by aP0THE0Sis on 2011-09-11
> **harlequin_ said:**
> 
Can you please open a terminal (click on the ubuntu icon at the top left of the screen, type "terminal" and press enter) and then type in it

```
unity --reset
```and then press enter? This will reset the unity to its default configuration (so if you made changes on the unity they will be reset). 



Thank You, Harlequin!

Its fixed now!  

Yeah, I was playing with the cube and it wasnt the same after that.
Everything seems to be working fine now!:popcorn:

---

### Post by wildmanne39 on 2011-09-11
Hi, you can use the link in my signature to set up the cube and effects, it has worked for everyone but one person that I know of.
Thank you

---

