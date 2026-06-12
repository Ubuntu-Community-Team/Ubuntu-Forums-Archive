---
title: "Optimizing CPU Usage"
date: 2009-07-23
forum: General Help
---

### Post by Pemdas on 2009-07-23
Hi, I've found most questions already answered on these forums, but I've finally come up against one that I think is worth asking about. 

I am on Ubuntu 8.10 and am attempting to get the best performance possible for some resource-intensive tasks. I am on a dual quad-core machine so there are 8 cores in total.

The application I am trying to optimize performance for is T-Coffee. It is designed to run in parallel and spwans 8 processes - one for each core. I expected the kernel to delegate these processes accross all cores, but instead I see one core maxed out at 100% usage (checked using top). 

Is this normal? To me it seems like several processors should work on these processes to avoid maxing out a single core. Perhaps I am misunderstanding the arcitecture. I am under the impression that 100% CPU refers to how much load the core is under, not processing speed. If a core has a 10% load, it is still executing instructions at the full clock speed, right?

Thanks in advance for any helpful responses.

---

### Post by Pemdas on 2009-07-23
Okay well I think I found the answer to my own question. I misunderstood how top reported CPU usage. The 8 percentages do not correspond to each core, they are the 8 states. It just so happens that I am using the same number of cores and was hence confused. 

So now my question is what is the most reliable way of checking how much load each core is under? I know system monitor exists, but isn't it quite resource intensive itself?

---

### Post by Finalfantasykid on 2009-07-23
htop provides more information compared to top, including how much load each cpu is under.

```
sudo apt-get install htop
```

---

### Post by Pemdas on 2009-07-23
Perfect, thanks.

---

