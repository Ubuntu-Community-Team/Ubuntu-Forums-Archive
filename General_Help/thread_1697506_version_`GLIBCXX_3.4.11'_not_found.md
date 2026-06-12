---
title: "version `GLIBCXX_3.4.11' not found"
date: 2011-02-28
forum: General Help
---

### Post by 1rick on 2011-02-28
Hey all. I'm a bit of a linux noob, running gOS (which I believe is based on 8.04) on a little Dell Mini (8GB SDD, hence gOS).

I tried installing an app called Sublime Text, and it yields the following error in terminal:

```
me@dellmini:~/apps/Sublime$ ./sublime_text
./sublime_text: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./sublime_text)
```

Naturally I've done a lot of Googling, and while I've found numerous suggestions I have yet to find any that make sense to me. Any suggestions?

---

### Post by dcstar on 2011-03-01
> **1rick said:**
> Hey all. I'm a bit of a linux noob, running gOS (which I believe is based on 8.04) on a little Dell Mini (8GB SDD, hence gOS).

I tried installing an app called Sublime Text, and it yields the following error in terminal:

```
me@dellmini:~/apps/Sublime$ ./sublime_text
./sublime_text: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./sublime_text)
```

Naturally I've done a lot of Googling, and while I've found numerous suggestions I have yet to find any that make sense to me. Any suggestions?

If that app requires a dependency that is not available in 8.04, then you cannot use it unless you install something to satisfy that dependency.

You may have to upgrade 8.04 to a later version that satisfies that dependency.

---

### Post by 1rick on 2011-03-01
Thanks David. 

I've tried running the latest netbook version of Ubuntu on this machine before, but found that the 8GB SSD is not quite big enough. It will install, but it throws 'hard drive is almost full' messages pretty quick.

---

