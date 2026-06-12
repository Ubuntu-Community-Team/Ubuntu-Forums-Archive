---
title: "Show time elapsed/remained in 'shred' terminal command?"
date: 2010-06-04
forum: General Help
---

### Post by inameiname on 2010-06-04
It is possible to not only have the progress of the shredding, but the time elapsed/remained/whatever as well? It would be great to be able to see the time elapsed/time remaining along with the percentage complete.

Is there any way?

---

### Post by KeyserSoze93 on 2010-06-04
```

man shred

```

```

shred -v

```

---

### Post by ryan858 on 2010-06-04
That just shows what pass it's on...

If you want to get into shell scripting, there are ways to do what you want. In fact, with scripting there is a way to do almost anything you could ever think of. And when (or if) you reach the limits of the shell language, you can move on to C, C++, and other, more powerful languages.

I personally find shell to be quite easy to use and pretty flexible/powerful. It's more than enough for my needs anyway. It's also easy to learn, and uses a lot of "makes-sense" kind of things.

---

### Post by Jeroensum on 2010-06-04
have a look at the *watch* command, together with a bit of scripting this might be able to accomplish what you want from it :)

---

### Post by inameiname on 2010-06-04
Thanks for all the suggestions. 

"-v" is what I currently use to show progress, percentage and what pass it's on, but for instance on a shredding of an entire hard drive of 500GBs, it'd also be nice to know without having to keep an eye on the clock how far it's progressed, and how much remains. 

I have made a few shell scripts before, but by no means an expert. I'll check out that 'watch' command though. Thanks.

---

