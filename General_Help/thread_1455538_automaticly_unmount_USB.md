---
title: "automaticly unmount USB"
date: 2010-04-16
forum: General Help
---

### Post by roderakker on 2010-04-16
Hey guys,

I'm working on this college project thing where I have to make a presentation-terminal. So far I managed to get into Ubuntu just enough that I could call myself a slightly-experienced user. I have gotten PowerPoint 2007 to work within Wine just fine, we chose not to use Open Office because we want the system to be user-friendly, and most computer-illiterate people don't know much about Open Office.

Now we've got a dilemma. We want the system to be kind of plug n' play-ish. Which is fine, because when you put your USB stick in the computer, a window will automaticly open showing all it's content, and the user will be able to easily present his presentation. (We will be limiting the OS alot, mostly by deleting most of the menus from the gnome panels, so people can only do the things related to presenting their presentation) But, the thing is, people will probably just pull out the USB stick when they're done, causing them to lose data but also causing the computer to get damaged, as it will be used more often than a normal home-computer.

I need to figure out how I can have the USB stick unmount after people close the presentation, and I was wondering if you guys might have any suggestions regarding this, or another idea that might come in handy. Scripts, tutorials or previously posted threads (I was not able to find any) are very welcome!

Thanks in advance,
roderakker

---

### Post by 3rdalbum on 2010-04-16
Two things:

1. The data on the USB stick will only be damaged if it is being written to. If the users are only running their presentations and not editing them, then it will not cause data loss to remove the stick without unmounting it.

2. You could enforce the need to not write to the sticks by making sure that they mount as read-only; or as "sync" rather than the default "async" (with 'sync' mode, data will be written to the device as soon as it is queued to be written; no buffering). I'm not sure how to do this, though, I think it can be done.

---

### Post by roderakker on 2010-04-16
> **3rdalbum said:**
> You could enforce the need to not write to the sticks by making sure that they mount as read-only; or as "sync" rather than the default "async".
Anybody have any idea how to do this? :D

---

### Post by dcstar on 2010-04-16
> **roderakker said:**
> Hey guys,

I'm working on this college project thing where I have to make a **presentation-terminal**. So far I managed to get into Ubuntu just enough that I could call myself a slightly-experienced user. I have gotten PowerPoint 2007 to work within Wine just fine, we chose not to use Open Office because we want the system to be user-friendly, and most computer-illiterate people don't know much about Open Office.
.........

And what's wrong with keyjnote?

---

### Post by roderakker on 2010-04-16
> **dcstar said:**
> And what's wrong with keyjnote?
I dont know what you mean, sorry. I've got most things figured out except for the unmounting thing..

---

### Post by roderakker on 2010-04-19
Anyone? Sorry for the selfish self-bump.

---

### Post by roderakker on 2010-04-19
Come on guys,
I know some of you will be able to help me out.

---

### Post by roderakker on 2010-04-22
badaaa-**bump**

---

### Post by roderakker on 2010-04-26
Thanks for the support. :)

---

