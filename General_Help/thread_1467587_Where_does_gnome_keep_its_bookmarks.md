---
title: "Where does gnome keep its bookmarks?"
date: 2010-04-30
forum: General Help
---

### Post by spoon_ on 2010-04-30
I just did a fresh install of lucid, and I'd like to transfer over all my bookmarks from karmic (sitting on another partition). Where are they stored? I'm talking about the things in the Places menu.

Thanks.

---

### Post by hansdown on 2010-04-30
Hi spoon_.

A fresh install will wipe all data on your HD.

Sorry.

---

### Post by spoon_ on 2010-04-30
No, I didn't delete my old install. The fresh install is actually on a brand new SSD I just got. I've mounted my old install's root directory (/) under /karmic.

I'd just like to know where under /karmic I should look to find my gnome bookmarks!

Thanks.

---

### Post by hansdown on 2010-04-30
Ah, good.
Try looking in places> home folder.

---

### Post by spoon_ on 2010-04-30
I guess I haven't clearly explained what I'm looking for. When I go to Places > Connect to Server, and then I tick off "Add bookmark", where does gnome keep that bookmark? I mean where in the filesystem is the list of all bookmarks that appear in the Places menu?

---

### Post by hansdown on 2010-04-30
Sorry if I'm not up to par here, but are you running a server?

If so, then I'm the last resort.

---

### Post by spoon_ on 2010-04-30
No, I'm not running server. I just used that as an example (when you connect to a server and tick off "add bookmark", it gets added as a bookmark). 

Anyways thanks for your help :)

---

### Post by hansdown on 2010-04-30
> **spoon_ said:**
> No, I'm not running server. I just used that as an example (when you connect to a server and tick off "add bookmark", it gets added as a bookmark). 

Anyways thanks for your help :)

Hope you find the answer.

---

### Post by spoon_ on 2010-04-30
Nope, not the firefox bookmarks. The bookmarks that appear in the Places menu in Ubuntu.

---

### Post by Vaphell on 2010-04-30
~/.gtk-bookmarks looks like it

---

### Post by spoon_ on 2010-05-01
> **Vaphell said:**
> ~/.gtk-bookmarks looks like it

Thanks, but my 9.10 installation doesn't have such a folder. I think it existed in previous versions of gnome/ubuntu.

---

### Post by WorMzy on 2010-05-01
It's not a folder, but a text file which stores one bookmark location per line.


Nice find, Vaphell.

---

### Post by spoon_ on 2010-05-01
Gah, thank you. I feel stupid :P

---

### Post by hansdown on 2010-05-01
> **spoon_ said:**
> Gah, thank you. I feel stupid :P

Relax. I feel the pain, also.

Thanks WorMzy.

---

### Post by spoon_ on 2010-05-01
> **hansdown said:**
> Relax. I feel the pain, also.

Thanks WorMzy.

Yeah we had quite a wacky communications breakdown there!

---

### Post by hansdown on 2010-05-01
> **spoon_ said:**
> Yeah we had quite a wacky communications breakdown there!

Haha!

It's all good.

Glad you got things sorted spoon_.

---

### Post by petermp on 2010-05-05
Side question; I use this functionality a lot, and really miss the possibility to organise the bookmarks more. Any tips?

---

