---
title: "Shell interprets tab at actual tab; no autocomplete"
date: 2009-08-28
forum: General Help
---

### Post by reemer on 2009-08-28
Hi there,

I'm an Ubuntu n00b with a problem.  On Ubuntu 8.1, I'm running bash with a $TERM of xterm-color. I've got three users on the box and two work fine in the sense that their shells work as you'd expect (tab autocompletes, colors are displayed, etc).  

The third is b0rked.  Examples:

* When I hit tab, it doesn't autocomplete; it adds a bunch of white space on the command line.  

* When I try to use a cursor key to scroll through text on the command line, I get the escaped versions of those characters (the left arrow, for example, prints ^[[D)

* the terminal is never in colour

I've copied the .bashrc from one of the working accounts and used it for the b0rked third one, and still no dice.  

Any help is very much appreciated. 

Thanks in advance!

---

### Post by Brandon Williams on 2009-08-29
Have you double-checked to make sure that the user's login shell was not changed? What does 'echo $SHELL' say? It's sounds like you're using /bin/sh, not /bin/bash.

---

### Post by uylug on 2009-08-29
What happens if you run this command

```
bash
```

And try again?

---

### Post by reemer on 2009-08-29
my shell was indeed /bin/sh, not /bin/bash.  changed it up and all is good.  thanks - this was bugging me for a few weeks!

really appreciate your help :)

---

### Post by uylug on 2009-08-29
Cool!

---

