---
title: "Disadvantages of upgrading ext3 to ext4"
date: 2010-01-02
forum: General Help
---

### Post by Dark Aspect on 2010-01-02
Hello,

I just upgrade my filesystem from ext3 to ext4 with no problems, however I was wondering are there any disadvantages from upgrading a filesystem in the long run. Is it as fast as a clean format?

BTW, I am on arch linux so this doesn't belong in the Ubuntu support area and I was mostly wanting opinions.

Thanks,

---

### Post by FuturePilot on 2010-01-02
> **Dark Aspect said:**
>  Is it as fast as a clean format?


No. The main disadvantage is that existing files won't be using extents. But over time as things are upgraded and whatnot they will eventually.

---

### Post by starcraft.man on 2010-01-02
The only serious disadvantage I can think of would be recovery tools that have not been upgraded to work with ext4 but do support ext3. There are still some I think. I can't comment on performance, not really that concerned with getting fastest in that area tbh. Long as data doesn't disappear.

---

### Post by CharmyBee on 2010-01-02
no big 512mb+ files. 'Shoot first, ask later' file writing.

---

### Post by insane_alien on 2010-01-02
> **CharmyBee said:**
> no big 512mb+ files. 'Shoot first, ask later' file writing.

eh? upgrading to ext4 doesn't stop you having >512MB files. and you can disable delayed allocation if you want.

---

### Post by FuturePilot on 2010-01-02
> **insane_alien said:**
> eh? upgrading to ext4 doesn't stop you having >512MB files. and you can disable delayed allocation if you want.

I'm pretty sure CharmyBee was referring to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579")

And disabling delayed allocation basically defeats the whole point of using Ext4 in the first place.

---

### Post by Dark Aspect on 2010-01-02
> **FuturePilot said:**
> I'm pretty sure CharmyBee was referring to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579")

And disabling delayed allocation basically defeats the whole point of using Ext4 in the first place.

The 2.6.32 Linux kernel fixed that problem according to my own research/googling. Ok so I can basically increase performance with:

```
find /home -xdev -type f -print0 | xargs -0 chattr +e
find /home -xdev -type d -print0 | xargs -0 chattr +e

```

Which rewrites all of the files.

Edit: Since the thread was moved......

> **Dark Aspect said:**
> 
BTW, I am on arch linux so this doesn't belong in the Ubuntu support area and I was mostly wanting opinions.

So I take it Ubuntu's forum supports Arch now?

---

