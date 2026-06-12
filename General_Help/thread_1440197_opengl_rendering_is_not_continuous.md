---
title: "opengl rendering is not continuous"
date: 2010-03-27
forum: General Help
---

### Post by mayankbhagya on 2010-03-27
Umm..

I have openGL working fine on my system.
The only problem is that when I try to run the executable file, nothing appears unless the full scene has been rendered.
In fact, it appears in parts, i.e. updates after a second, then after another second etc...
However, earlier, the rendering used to be continuous and I could see each pixel getting rendered in a continuous fashion.

Anyone?

Also, it when I run the executable for the first time, it is rendered twice.. any ideas why?

---

### Post by ethoxyethaan on 2010-03-27
What executable are you talking about?

---

### Post by mayankbhagya on 2010-03-27
the executable is what i've compiled from a simple openGL code that I wrote.

It used to work fine a few days back.. but, if I enabled Desktop effects (compiz) it used to interfere with the rendering...

So the display buffer is not updated continually, however, after gaps of around 2 seconds..

So I can see partial outputs... say for e.g.
0% then 20% then 40% then 60% then 80% and then the full output.
However, earlier, while rendering, this transition was continuous rather than discrete...

---

### Post by mayankbhagya on 2010-03-28
ok I found it..
I had to use glFlush() at the right place.
:)

---

