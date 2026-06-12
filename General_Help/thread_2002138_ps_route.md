---
title: "ps route"
date: 2012-06-12
forum: General Help
---

### Post by cucuru on 2012-06-12
hello! I have some processes runing in my ubuntu. All of them are SCREEN with java.

one of them is 

```

 java /java/java spb.init


```

and the other one:

```

java /javapruebas/java spb.init

```


and I need to know which is each one:


```

ubuntu@ubuntu:~/javapruebas$ ps -u
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ubuntu    2903  0.0  4.8 454752 49416 pts/1    Ssl+ Jun08   4:21 java spb.init
ubuntu    3054  0.1  4.5 442660 46672 pts/2    Ssl+ Jun08   5:58 java spb.init
ubuntu    3188 49.3  2.4 412020 25596 pts/3    Ssl+ Jun08 2800:46 java spb.init
ubuntu   30601  0.0  0.5   9244  5984 pts/0    Ss   08:20   0:00 -bash
ubuntu   32036  0.0  0.5   9240  5848 pts/4    Ss   09:08   0:00 -bash
ubuntu   32594  0.0  0.1   4588  1096 pts/0    R+   09:29   0:00 ps -u



```

How can I know this?

Thank you in advance

---

### Post by Cheesehead on 2012-06-12
'ps -aux' will show the entire command path.
(Tip: if possible, widen your terminal window)

---

### Post by cucuru on 2012-06-12
Thanks, but I've already tried that, doesn't work:

```


ubuntu    2902  0.0  0.1   5172  1120 ?        Ss   Jun08   0:01 SCREEN java spb.init
ubuntu    2903  0.0  4.9 456372 50420 pts/1    Ssl+ Jun08   4:43 java spb.init
ubuntu    3053  0.0  0.1   5172  1104 ?        Ss   Jun08   0:02 SCREEN java spb.init
ubuntu    3054  0.1  4.5 444440 46748 pts/2    Ssl+ Jun08   6:29 java spb.init
ubuntu    3187 13.2  0.1   5172  1112 ?        Ss   Jun08 815:50 SCREEN java spb.init
ubuntu    3188 49.4  2.4 412020 24652 pts/3    Ssl+ Jun08 3039:17 java spb.init


```

Any other option? thank you!

---

