---
title: "What is actually used and needed in my kernel config?"
date: 2010-06-04
forum: General Help
---

### Post by koe1974 on 2010-06-04
I would like to compile my own kernel. I am familiar with how to do it and have done it in the past so I'm not looking for a how to compile a kernel. 

In the kernel config are many, many options. In the past when I compiled kernels I always wondered about what is needed and used. 

What is the best way to determine what is currently used, not set or enabled in the existing config, but actually used by my existing kernel?

I have a general idea of what is loaded and could do trial and error, turn this and that off, recompile, etc but is there an easier way?

---

### Post by Boondoklife on 2010-06-04
Really short of trial and error the best way is to look at your hardware and what it supports/can do, and what you want to do. Once you have this information together then go through the kernel config, branch by branch, and select the needed options.

I used to do this with a Gentoo server I ran and it worked out great. It can be a pain to figure out what modules support your hardware so lace up your google shoes before hand.

---

### Post by sandyd on 2010-06-04
the command "lsmod" will list all the modules currently in use.

---

### Post by koe1974 on 2010-06-04
Yes, when I did LFS a few years ago it required a lot of time, poking, reading etc. Thanks for the reassurance that it is a matter of research and, trial and error. I was hoping someone might had developed something that just generates a config based on hardware or a running kernel.

And so it begins!

---

