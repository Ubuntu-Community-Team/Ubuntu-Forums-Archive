---
title: "How to execute a .bin file from assembly code"
date: 2011-11-24
forum: General Help
---

### Post by /bin/sh on 2011-11-24
Hi all.
I need to make a system call in assembly that will execute a .bin file(an assembly file which is assembled). I have checked all over the internet but I have not found a single page that tells how to do it.
Please tell me how to do this.

---

### Post by frostyfrog2 on 2011-11-24
Just a guess but...

```

chmod +x somefile.bin
./somefile.bin

```

---

### Post by /bin/sh on 2011-11-25
> **frostyfrog2 said:**
> Just a guess but...

```

chmod +x somefile.bin
./somefile.bin

```

That is shell script, I meant assembly. I need to load and execute .bin files in assembly like an os loads them.

---

