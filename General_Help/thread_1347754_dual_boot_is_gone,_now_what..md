---
title: "dual boot is gone, now what."
date: 2009-12-06
forum: General Help
---

### Post by cogene on 2009-12-06
Last summer I loaded ubuntu 9.04 on my HP laptop as a duel boot with windows XP pro.
everything worked just fine and I could enjoy the best of both worlds. I was very happy to say the least.
Today I updated the ubuntu O.S. and when it rebooted the duel boot option is gone, no more windows XP. 
Ubuntu is fine but what do I need to do to get the XP dual boot option back?

James

[email]cogene3@gmail.com[/email]

---

### Post by Altay_H on 2009-12-06
Did you upgrade from 9.04 to 9.10? If so, the following two terminal commands might help bring back XP.

First, make sure other operating systems are enabled by running the following line:
```
sudo chmod +x /etc/grub.d/30_os-prober
```

Then update your boot manager by running the following line:
```
sudo update-grub
```

**Don't try this if you're still using 9.04.**

---

### Post by ranch hand on 2009-12-06
What kind of upgrade did you do?

If it was an upgrade from 9.04 you should still be using grub-legacy.

If it was a clean install you are using grub2.

Post the results of;
```

grub-install -v

```
and we will go from there.

---

