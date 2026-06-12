---
title: "To low on memory to send crash report..."
date: 2012-07-21
forum: General Help
---

### Post by brad1138 on 2012-07-21
I keep getting this message:

[I]"Sorry, the program "chromium-browser" closed unexpectedly

Your computer does not have enough free memory to automatically 
analyze the problem and send a report to the developers."[/I]

I run Xubuntu on my older Compaq V5000 laptop (v5209 to be precise) with Celeron M CPU and 1 GB of memory. I get this message even when total memory usage is around 20-25%. I use Xubuntu because it is supposed to do well on older machines. I would think 1 GB would be more than enough ram.

Any ideas?

---

### Post by Peripheral Visionary on 2012-07-22
I run Xubu on an older computer with half as much RAM as yours, and it's nice and quick, no issues like yours. Perhaps it's a Chromium thing, but it's unlikely that the statement, "*Your computer does not have enough free memory to automatically analyze the problem and send a report" *is actually the case.

Try experimenting with another browser (Midori is awesome now, I suggest that one) and see if you still have the same issue.

---

### Post by Elfy on 2012-07-22
try from a terminal

```
ubuntu-bug chromium-browser
```

Also - have a look here - which suggest it's not memory but space [img]https://encrypted-tbn1.google.com/images?q=tbn:ANd9GcRIVkF7qKUB7pa8CkJtA0khkoEfPpcrCFdKUtCcuD-d13gTuUjG3Q[/img]

---

### Post by brad1138 on 2012-07-23
> **Elfy said:**
> try from a terminal

```
ubuntu-bug chromium-browser
```

Also - have a look here - which suggest it's not memory but space [img]https://encrypted-tbn1.google.com/images?q=tbn:ANd9GcRIVkF7qKUB7pa8CkJtA0khkoEfPpcrCFdKUtCcuD-d13gTuUjG3Q[/img]

Have a look where?

---

### Post by Elfy on 2012-07-24
Whoops - now I can't find the bug again :(

---

### Post by brad1138 on 2012-07-25
I just uninsalled chromium and went back to FireFox. My computer is much less bogged down all the time (I always have a browser open). I like Chrome/Chromium, but I like FF also and this is the esiest fix.

Thanks for the replies.

---

