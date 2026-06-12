---
title: "Grub 2 not loading newest kernel"
date: 2010-03-20
forum: General Help
---

### Post by agentsmith23 on 2010-03-20
I have been running Ubuntu 9.10 ever since it was released, on my HTPC. However, for some reason when a new kernel comes out and I upgrade to it GRUB 2 doesn't load the newest kernel but just loads the old original kernel that came with it when I originally installed 9.10. I have confirmed that the newer kernels are installed by editing the GRUB 2 command line at startup (just a temporary fix) and all worked well with the newer kernels. How can I make GRUB 2 load the newest kernel by default. On my laptop running 9.10 it has loaded the newest kernel by default ever since I installed it but my HTPC just won't cooperate.

Please help! 
Thanks!

---

### Post by zvacet on 2010-03-21
Did you tried with 

```
sudo update-grub
```

---

### Post by agentsmith23 on 2010-03-21
> **zvacet said:**
> Did you tried with 

```
sudo update-grub
```

Yes, I tried that and it shows all of the kernels but it still loads the oldest one.

---

### Post by agentsmith23 on 2010-03-22
I feel dumb now. I always thought grub2 was installed with 9.10 no matter what. But I found [_[COLOR="Red"]here[/COLOR]_]("https://wiki.ubuntu.com/Grub2") that if you upgraded from 9.04 that you have to manually upgrade to grub2. So i followed the instructions for upgrading and everything works fine now.

---

