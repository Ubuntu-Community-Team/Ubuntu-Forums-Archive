---
title: "What exactly is swappiness?"
date: 2010-06-11
forum: General Help
---

### Post by josephellengar on 2010-06-11
My swappiness:

```

cat /proc/sys/vm/swappiness

```

is 60.  What does this mean and should I change it?  I'm guessing it has something to do with the swap file so you might want to know that I have 8gb of ram and a 12gb swap file.  Thanks!

---

### Post by john newbuntu on 2010-06-11
This explains it:
[https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")

I have hardly seen the swap being used on my laptop having 1GB RAM and yet I set it to 10.

---

### Post by dcstar on 2010-06-12
> **john newbuntu said:**
> 
........
I have hardly seen the swap being used on my laptop having 1GB RAM and yet I set it to 10.

Der. The **lower** the setting the **less** Swap will ever be used.

---

### Post by john newbuntu on 2010-06-12
@dc : You are correct. What I actually meant was that even with the default swappiness, I hardly ever saw the swap being used after prolonged monitoring.  Despite that I reduced it to 10.

---

### Post by NightwishFan on 2010-06-12
If you set your swappiness to 0, it will still use swap when needed. If you set it to 100, it will not always use swap. So I usually advise users to set the value to 100, so the system will perform better when under memory pressure. The default value is fine though.

---

### Post by dcstar on 2010-06-12
> **NightwishFan said:**
> If you set your swappiness to 0, it will still use swap when needed. If you set it to 100, it will not always use swap. So I usually advise users to set the value to 100, so the system will perform better when under memory pressure. The default value is fine though.

Advising people to set that to 100 will almost always result in **worse** performance as more swap is used to make space for cache and you end up waiting for more program code to be swapped back into RAM for execution.

People with performance issues are advised to reduce that setting and they invariably report that the reduction has reduced their problems.

---

### Post by NightwishFan on 2010-06-12
They are incorrect as I have tested it under memory pressure. It is nearly the same with a swappiness of 100, my swap is never used.

---

### Post by dcstar on 2010-06-13
> **NightwishFan said:**
> They are incorrect as I have tested it under memory pressure. It is nearly the same with a swappiness of 100, my swap is never used.

If your Swap is **never** used, then you probably don't even have it enabled.

I have 4GB RAM and my swap is** rarely** used, only when I am running multiple simultaneous VMs.

---

### Post by NightwishFan on 2010-06-13
I am not a moron. I know my swap is enabled. I am talking about things I have actually tested. :)

---

