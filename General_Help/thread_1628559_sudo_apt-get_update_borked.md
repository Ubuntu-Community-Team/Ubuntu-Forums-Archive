---
title: "sudo apt-get update borked"
date: 2010-11-22
forum: General Help
---

### Post by Theist17 on 2010-11-22
Guys, I have no idea what's going on here. I'm totally at a loss. I've been using Ubuntu for three years now and have never ever seen this before. 

```

evan@laptop:~$ sudo apt-get update
E: Type '&#8220;deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
```

EDIT: 

Found the problem, which took all of five seconds to fix. Somehow, a weird little source wormed its way into my sources.list
Still trying to suss that one out.

---

### Post by dcstar on 2010-11-23
> **Theist17 said:**
> Guys, I have no idea what's going on here. I'm totally at a loss. I've been using Ubuntu for three years now and have never ever seen this before. 

```

evan@laptop:~$ sudo apt-get update
E: Type '“deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
```

EDIT: 

Found the problem, which took all of five seconds to fix. Somehow, a weird little source wormed its way into my sources.list
Still trying to suss that one out.

So it is **solved** then?

---

### Post by Theist17 on 2010-11-25
Sorry, in my rush to make new problems for myself, I forgot to mark the thread. Thanks for the reminder!

---

