---
title: "How to know apt-get package name?"
date: 2010-06-18
forum: General Help
---

### Post by UranUtan on 2010-06-18
Hi,

Most of the time, when I need something, there is a magic **sudo apt-get install something**

Generally I make some searches and found either a forum post or a blog post where someone give the complete syntax of "sudo apt-get install ...etc..."

But how do these people know the exact package name?

---

### Post by J V on 2010-06-18
Word of mouth... I probably know over 100 package names out of my head by now.

Of course, you could just open synaptic package manager or the software center and do a search, which should reveal the package as well...

---

### Post by bodhi.zazen on 2010-06-18
You can try apt-search

```
apt-cache search foo
```

I also find synaptic helpful, you can search for packages with synaptic as well.

If all else fails, google.

---

### Post by UranUtan on 2010-06-18
Hi,

Thanks for your quick help. It's cool that apt-cache search syntax. However, in my opinion, it would make sense to call it "apt-get search" instead of "apt-cache search"

The implementation behind cache or get that apt would do is not that important from the end user perspective.

---

### Post by bodhi.zazen on 2010-06-18
> **UranUtan said:**
> Hi,

Thanks for your quick help. It's cool that apt-cache search syntax. However, in my opinion, it would make sense to call it "apt-get search" instead of "apt-cache search"

The implementation behind cache or get that apt would do is not that important from the end user perspective.

+1 , it took me some getting used to as well.

---

