---
title: "Which is accurate Conky or system monitor?"
date: 2010-09-02
forum: General Help
---

### Post by Mr_VeRiTy on 2010-09-02
Hi, I read in a forum a while ago that system monitor was inaccurate,and I was wondering if that was true. I ask because when using blender for 3d modeling Conky says 2.53GiB out of 3.81GiB of RAM is used, but system monitor says that 1.2GiB is used, and I was wondering which one to trust.

---

### Post by Morrad on 2010-09-02
It sounds as though on your system Conky may be configured to include buffered or cached memory along with the actively used memory.

You could try popping open a terminal and running:

```
free -m
```

This will show you (in MB) how much memory is being used, and how, in your system.

---

### Post by Mr_VeRiTy on 2010-09-02
> **Morrad said:**
> It sounds as though on your system Conky may be configured to include buffered or cached memory along with the actively used memory.

You could try popping open a terminal and running:

```
free -m
```

This will show you (in MB) how much memory is being used, and how, in your system.
Thanks, it appears that Conky is the most accurate, as "free -m" showed 2600MB of RAM was used.

---

### Post by Morrad on 2010-09-02
> **Mr_VeRiTy said:**
> Thanks, it appears that Conky is the most accurate, as "free -m" showed 2600MB of RAM was used.

I wanted to point out to you that they may both be accurate, but they're reporting different things.  I should have given more explanation when I first posted.

The cache includes some information from programs that you've run recently.  For example, if I close Firefox, some of the Firefox binary stays in cache memory.  When I start up Firefox again, it loads faster since that information doesn't have to be loaded into RAM from the disk, since it's already there.

Let me illustrate with my system memory state right now.

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1660        348          0         53        915
-/+ buffers/cache:        691       1317
Swap:         2863          0       2863

```

So for my system, there are 1660MB of RAM being used right now (total, both cache and running programs).  But only 691MB are currently being used by running programs.

---

### Post by Mr_VeRiTy on 2010-09-02
> **Morrad said:**
> I wanted to point out to you that they may both be accurate, but they're reporting different things.  I should have given more explanation when I first posted.

The cache includes some information from programs that you've run recently.  For example, if I close Firefox, some of the Firefox binary stays in cache memory.  When I start up Firefox again, it loads faster since that information doesn't have to be loaded into RAM from the disk, since it's already there.

Let me illustrate with my system memory state right now.

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1660        348          0         53        915
-/+ buffers/cache:        691       1317
Swap:         2863          0       2863

```

So for my system, there are 1660MB of RAM being used right now (total, both cache and running programs).  But only 691MB are currently being used by running programs.
Ahh I see, So system monitor is just telling me how much ram is being used currently and conky is telling me how much is cached a well as how much is being used. Thanks for clearing that up.

---

