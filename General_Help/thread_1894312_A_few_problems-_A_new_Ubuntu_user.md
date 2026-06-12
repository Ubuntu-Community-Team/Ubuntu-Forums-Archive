---
title: "A few problems- A new Ubuntu user"
date: 2011-12-12
forum: General Help
---

### Post by lenovo x61 on 2011-12-12
Hello all, I am totally new to ubuntu and linux. I am currently using ubuntu 10.04 (for macbuntu)

I accidentally messed with my text settings in the appearance box. Now my text is really fuzzy and not crisp as before. I am using a Lenovo x61 (non-tablet version) and the resolution is 1024x768. I don't know my ppi so I don't know where to adjust it.

My second problem is that my panel is weird. the spaces between the icons is reallllly big. I tried moving them tighter but it does not work. I am using macbuntu (the transformation pack) if that helps.

My third problem is that openoffice writer saves .doc files fine. But when I restarted, I found out that my 3500 word history essay file is EMPTY!!! I wanted to save as a .doc so I can open it on my iMac's microsoft office. But when I restarted and checked before sending it to myself, it is 0bytes and empty.

Also I cannot change my mouse cursors??

Looking forward for any suggestions and replies!

Thanks!

---

### Post by Frogs Hair on 2011-12-12
I am not familiar with Macbuntu , but when you open fonts in appearance preferences try the different font  rendering options on the bottom .  There is sub pixel smoothing among other options .

The cursor options in the default 10.04 installations is found appearance preferences > themes > customize . I have no idea how Macbuntu may or may not be be affecting your ability to change settings since it is an unofficial theme / application .

---

### Post by The Cog on 2011-12-12
> **lenovo x61 said:**
> My third problem is that openoffice writer saves .doc files fine. But when I restarted, I found out that my 3500 word history essay file is EMPTY!!! I wanted to save as a .doc so I can open it on my iMac's microsoft office. But when I restarted and checked before sending it to myself, it is 0bytes and empty.That is seriously inconvenient. Try enabling the showing of hidden files (often Ctrl-H but I don't know macbuntu) and see if openoffice has left any old backup copies there. If you find something suitable-looking, you can copy and paste it to a .doc name and then try to open it.

Good luck.

---

### Post by lenovo x61 on 2011-12-13
Thanks to all the people who replied. 

The Cog, I tried looking at the hidden files but I have no luck. I just re-wrote the whole essay instead :(.

Thanks everybody who helped me!

---

### Post by Mark Phelps on 2011-12-13
Sorry, I'm not at my home PC so I don't have the bug report link ... but that is a known bug that results in files being zeroed-out on EXT4 filesystems.  It happened to me twice in recent times -- and even though I had autosave turned on.

In future, you should manually make a backup of your documents using a different filename.  I did that so that, even if the original document gets zeroed-out, you will have the other to work from.

---

