---
title: "Slow performance"
date: 2010-06-03
forum: General Help
---

### Post by YigalB on 2010-06-03
Lately I noticed my Ubuntu is slowing down. I installed the 10.04 from scratch (including hdisk format), and still ut's very slow.It's a dual CPU P4 2.8GHz with 1GB DRAM, 120GB hard drive (SATA connected).
The CPU doesnt look very loaded most of the time, yet even moving a window on the screen requires few seconds of waiting.

Any idea why?
Is there a utility that analyse the performance?

---

### Post by wojox on 2010-06-03
What do you have for Graphics?

```
lspci | grep VGA
```

---

### Post by YigalB on 2010-06-03
> **wojox said:**
> What do you have for Graphics?

```
lspci | grep VGA
```

I don't understand the question.

---

### Post by tankjer on 2010-06-03
> **YigalB said:**
> I don't understand the question.
What graphics card do you have? If you don't know then run the command in terminal that wojox wrote.

---

### Post by YigalB on 2010-06-03
> **wojox said:**
> What do you have for Graphics?

```
lspci | grep VGA
```

VGA compatible controller: ATI RV535 (Radeon X1650 series) (rev 9e)

---

