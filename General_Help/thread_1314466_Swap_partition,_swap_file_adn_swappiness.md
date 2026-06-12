---
title: "Swap partition, swap file adn swappiness ???"
date: 2009-11-04
forum: General Help
---

### Post by Flywaver on 2009-11-04
Greetings,

I have recently installed 9.10 from fresh and I created a swap partition. Now, I read the Ubuntu SwapFaq and created a swap file of 3Gb (double the amount of RAM I have) and enabled it. I can see it fine when I do ```
cat /proc/meminfo
```

Now, I read about swappiness and that Ubuntu set it to a default value of 60...having a 3Gb SWAP file, do I need to lower this or not? 

I don't want to end up having more swapping than RAM usage! I have 1.5Gb RAM but it's average DDR400 RAM and when I load a lot of apps the system goes busy! 

Any help yould be appreciated! :)

Cheers!

---

### Post by jmszr on 2009-11-04
Flywaver,

For desktop use swappiness=10 is recommended per: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) . The discussion is about 3/4 of the way down.

---

### Post by Flywaver on 2009-11-04
> **jmszr said:**
> Flywaver,

For desktop use swappiness=10 is recommended per: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) . The discussion is about 3/4 of the way down.

Thanks jmszr! :)

---

