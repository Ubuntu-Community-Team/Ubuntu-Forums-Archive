---
title: "Search Programs by Date"
date: 2010-09-12
forum: General Help
---

### Post by calskin on 2010-09-12
Hi, total newb here.

I'm wondering if there's a way to search installed programs by when they were installed?  On Friday, I installed a bunch of programs and I can't remember exactly what all of them were, but I don't like the way my system has been acting since.

---

### Post by llamabr on 2010-09-12
I don't see that option in dpkg-query, though you might look more closely.

You might be able to find it in your ~/.bash_history

I think it saves your last 500 commands.  It's a kinda backwards way to solve your problem, but in the hope that it helps...

---

### Post by sikander3786 on 2010-09-12
```

cat /var/log/dpkg.log | grep "\ install\ "

```

does the trick for me.

---

### Post by sgage on 2010-09-12
Synaptic has a "history" browser under the File menu. It can be very handy.

---

### Post by calskin on 2010-09-12
> **llamabr said:**
> You might be able to find it in your ~/.bash_history

Thanks, but it didn't work for me.  The command wasn't found.

---

### Post by calskin on 2010-09-12
> **sgage said:**
> Synaptic has a "history" browser under the File menu. It can be very handy.

Thanks, that was exactly what I was looking for.

---

### Post by calskin on 2010-09-12
> **sikander3786 said:**
> ```

cat /var/log/dpkg.log | grep "\ install\ "

```

does the trick for me.

Thanks, this was an equally helpful answer

Thanks for such quick replies too.

---

