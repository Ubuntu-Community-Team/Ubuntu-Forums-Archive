---
title: "Why isn't preload enabled by default?"
date: 2011-08-13
forum: General Help
---

### Post by Jamsers on 2011-08-13
Quick question: Why isn't preload enabled/installed by default in Ubuntu? Tried googling it, didn't really find anything apart from "it increases boot up time a bit".

---

### Post by mcduck on 2011-08-13
That's pretty much the reason. You only get benefits from preload if you most of the time use a fairly small selection of programs, and tend to always open all of them when you start your computer.

On the other hand if the task you do on your computer and the programs you are using vary a lot, preloading would just make the boot time slower and load bunch of stuff you aren't going to use into memory.

The added boot time and the cost of using more RAM right from the boot would be especially noticeable on low-end machines, while Ubuntu tries to support such systems as well as possible.

So it's a feature that benefits some people, while at the same time decreases the performance for others. Since it's pretty easy to enable, it's left up to users to start using it if they think their computer usage falls into the cases where preloading would be beneficial.

---

### Post by Jamsers on 2011-08-15
Thanks! Now I think I should disable preload, since the stuff I do on my computer varies a lot. Turns out I'm just unnecessarily lengthening the boot time. :-)

---

