---
title: "cd not working properly?"
date: 2010-11-18
forum: General Help
---

### Post by Kocrachon on 2010-11-18
Ok, so I am trying to cd to a folder

specifically /home/kocrachon/d20

I was under the impression I could do

cd home/kocrachon/d20

instead I had to do cd /kocrachon/  cd /d20

What am I doing wrong?

---

### Post by lisati on 2010-11-18
> **Kocrachon said:**
> Ok, so I am trying to cd to a folder

specifically /home/kocrachon/d20

I was under the impression I could do

cd home/kocrachon/d20

instead I had to do cd /kocrachon/  cd /d20

What am I doing wrong?

Try this with an extra "/" at the start:
```
cd /home/kocrachon/d20
```

---

### Post by amauk on 2010-11-18
Either```
cd /home/kocrachon/d20
```Or, assuming you're logged in as user "kocrachon"
```
cd ~/d20
```

---

### Post by Kocrachon on 2010-11-18
Thanks...

I feel like a noob now -_- been using ubuntu for a while... forgot how to navigate...

---

### Post by lisati on 2010-11-19
> **Kocrachon said:**
> Thanks...

I feel like a noob now -_- been using ubuntu for a while... forgot how to navigate...

Don't panic! it can happen from time to time.

---

