---
title: "Crazy Memory Usage?"
date: 2009-09-29
forum: General Help
---

### Post by afderrick on 2009-09-29
OKay, so here is the story.  My memory usage looks oddly crazy.  Wondering if anyone has seen this and what exactly to do about it.

I have 2GB (2x 1GB) memory in my computer.

If I open up system monitor I see something like this...
Memory 778.1 MiB (38%) of 2.0 GiB  
Swap 78 (3.8%) of 2.0Gib

If I open up a terminal and type top, I see something like this.
Mem:   2060704k total,  1919888k used,   140816k free,   217064k buffers
Swap:  2104472k total,    80644k used,  2023828k free,   910304k cached


which is way off from what system monitor is showing.  By a LONG shot unless I am reading these numbers very very wrong.  Can someone help?

---

### Post by mac9416 on 2009-09-29
Hey afderrik. That is certainly way too much RAM usage. Let's see just how much RAM each process is using. Try running this command and pasting the output here...
```
ps -e -orss=,args= | sort -b -k1,1n | pr -TW$COLUMNS
```

---

### Post by undecim on 2009-09-29
The reason for this is that your system monitor doesn't take into account cached files. The kernel will keep some files (or other filesystem information) in ram if there is the ram to spare. The reason the system monitor doesn't care about this is because as soon as another application needs that memory, the kernel will free it up. (that's why having more ram than you actually use can make your system faster -- copies of commonly used files stick in the extra ram)

really, the ram usage that top is reporting shouldn't be anything to worry about.

---

### Post by Slim Odds on 2009-09-29
Search the forums a little, this topic comes up ALL THE TIME.

---

### Post by blackened on 2009-09-29
> **Slim Odds said:**
> Search the forums a little, this topic comes up ALL THE TIME.

+1. What you're experiencing is completely normal. As already suggested, search the forums.

---

### Post by Mighty_Joe on 2009-09-30
[Linux Ate My RAM]("http://www.linuxatemyram.com/")

---

