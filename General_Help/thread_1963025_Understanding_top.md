---
title: "Understanding top"
date: 2012-04-21
forum: General Help
---

### Post by hojjat on 2012-04-21
I just ran this command in R, which takes a long time to process all data. In the meantime I ran *top* to see how CPU is being utilized.

In the bottom part, where processes are listed, the CPU value for R was 100%. However, in the top part, were a summary of all resources was given, it read: 
```

6.0%us,  0.1%sy,  0.0%ni, 93.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

```

which, if I understand correctly, means that 93% of the CPU resources are in idle mode. Am I understanding this correctly? If yes, how come R is using 100% CPU yet utilizing only 6% of computation resources? And how can I increase that to, say, 25% (i.e. using 100% of one of the four CPU cores?)

Please note that my R commands do not support multicore processing.

---

### Post by SeijiSensei on 2012-04-22
> **hojjat said:**
> Please note that my R commands do not support multicore processing.

That's probably the reason right there.  In top, if you hit the "1" key, you'll expand the processor load figures to show each core.  The result will look like this:

```

Cpu0  :  0.7%us,  0.7%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Cpu1  :  0.0%us,  0.7%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.7%us,  1.0%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

```

My guess is that, lacking support for multiple cores, you'll see one that is heavily loaded while the others remain relatively idle.

---

