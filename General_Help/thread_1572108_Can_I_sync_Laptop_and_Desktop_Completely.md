---
title: "Can I sync Laptop and Desktop Completely?"
date: 2010-09-10
forum: General Help
---

### Post by SteveDhalai on 2010-09-10
Hey,

I currently run Ubuntu on my desktop and have just ordered a netbook which I intend on installing Ubuntu on.

I was wondering if it was possible to keep both machines completely in sync ie, same files on both (music, pictures, desktop, documents etc) same settings, same themes, same programs etc etc?

Files is my main priority, I would like the same files to be on both so I am never missing anything.

Is anything like this possible?

Thanks,
Steve.

---

### Post by surfer on 2010-09-10
```

$ rsync -avz --exclude '.*' user@machine:/home/user /home/user

```
should sync your documents (excluding the configuration files; i'd recommend to be careful with the .* directories). test this first! i haven't...

---

### Post by surfer on 2010-09-10
oh, and if you add the [FONT="Courier New"]--delete[/FONT] switch, non-existing files on the first host will be deleted on the second one.

---

