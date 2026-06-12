---
title: "CPU 100% all the time.."
date: 2010-09-09
forum: General Help
---

### Post by Codone on 2010-09-09
I'm not very experianced with ubuntu and recently installed it on a Compaq Presario SR1611NX.
When I open system monitor it says cpu is at 100% and rarely drops lower.

AMD Sempron 3200+ Processor
512mb ram
53% Memory usage with just Firefox open
8.9% Swap memory out of 1.2 gig used

Please help

---

### Post by 3Miro on 2010-09-09
Go to System -> Admin -> System Monitor to find the process that is stealing your CPU.

You can also go to the Terminal (Apps -> Accessories -> Terminal) and type:
```
top
```

---

### Post by 98cwitr on 2010-09-09
or you can just go under the processes tab and sort by usage :)

---

### Post by philinux on 2010-09-09
> **Codone said:**
> I'm not very experianced with ubuntu and recently installed it on a Compaq Presario SR1611NX.
When I open system monitor it says cpu is at 100% and rarely drops lower.

AMD Sempron 3200+ Processor
512mb ram
53% Memory usage with just Firefox open
8.9% Swap memory out of 1.2 gig used

Please help

Apart from the cpu problem the other stuff is perfectly normal. With only 512mb ram it's bound to use swap.
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

---

### Post by Codone on 2010-09-09
> **3Miro said:**
> Go to System -> Admin -> System Monitor to find the process that is stealing your CPU.

You can also go to the Terminal (Apps -> Accessories -> Terminal) and type:
```
top
```

Quick responses thanks!
and I went through system monitor and it said it was mainly firefox, buuut I realized the case was upside down so I flipped it right side up and it seems to be working smoother now :o
Case is all tore apart so couldnt tell at first hah.

---

### Post by talvik on 2010-09-09
> **Codone said:**
> I realized the case was upside down so I flipped it right side up and it seems to be working smoother now :o
Case is all tore apart so couldnt tell at first hah.

Case? Your computer case?

Probably was a web site with buggy javascript or maybe flash.

Google for NoScript and/or flashblock for firefox, and see if one of them fits you. Really recommend if you use a LOT of tabs.

---

