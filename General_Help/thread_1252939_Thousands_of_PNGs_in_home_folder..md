---
title: "Thousands of PNGs in home folder."
date: 2009-08-29
forum: General Help
---

### Post by GeneralHooHa on 2009-08-29
Hey Ubuntuforums,

I was using some DVD creator (forgot the name), canceled its progress, and somehow ended up with thousands of .PNGs in my home folder (00175586.png, 00175587.png, etc.)

It takes forever to load, I tried "sudo rm -r ~/00*", but it said there was too much to remove ( sudo: unable to execute /bin/rm: Argument list too long )

Whats the best way of deleting all of these images out of my folder?

---

### Post by mali2297 on 2009-08-29
Try a loop,
```

for i in ~/00*.png; do rm $i; done

```

---

### Post by GeneralHooHa on 2009-08-29
> **mali2297 said:**
> Try a loop,
```

for i in ~/00*.png; do rm $i; done

```

That did the trick... thanks mucho

---

