---
title: "Netcat output pipes and redirection"
date: 2010-05-25
forum: General Help
---

### Post by Zrc on 2010-05-25
I'm trying to redirect nc command output but I can't do it.

I have tried this:

nc -z -v -w1 hostip 1-1000>> hostip.txt

And this:

nc -z -v -w1 hostip 1-1000| grep -v ?

But it seems doesn't work. What's the problem?

---

### Post by Zrc on 2010-05-25
> **Zrc said:**
> I'm trying to redirect nc command output but I can't do it.

I have tried this:

nc -z -v -w1 hostip 1-1000>> hostip.txt

And this:

nc -z -v -w1 hostip 1-1000| grep -v ?

But it seems doesn't work. What's the problem?


Well, I can do:

nc -z -v -w1 hostip &>> hostip.txt

But I still need to grep the output.

---

### Post by gmargo on 2010-05-25
netcat is writing to stderr, so redirect stderr into stdout like this:
```

$ nc -z -v -w 1 127.0.0.1 1-1000 2>&1 | grep -v '?'

```

---

### Post by Zrc on 2010-05-26
Thanks gmargo.

I've checked and works as I need.

---

