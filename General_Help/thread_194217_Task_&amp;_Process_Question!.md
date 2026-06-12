---
title: "Task &amp; Process Question!"
date: 2006-06-11
forum: General Help
---

### Post by wdbreen on 2006-06-11
Gday All,
I just done a *top* command and noticed along with the other stats, one called a zombie.
What is this?
Is it a normal process that runs on all ubuntu machines?

Breeny

---

### Post by ayoli on 2006-06-11
A zombie process isn't really a process at all- it's just what's left over after it died and doesn't react to signals. What's supposed to happen is that its parent process was to issue a "wait()" to collect the information about its exit. If the parent doesn't (programming error or just bad programming), you get a zombie. The zombie will go away if its parent dies- it will be "adopted" by init which will do the wait()- so if you see one hanging about, check its parent, if it is init, it will be gone soon, if not the only recourse is to kill the parent..which you may or may not want to do.
So you can find zombie processes on any machine, any distribution.
hope that's answering your question ;)

---

