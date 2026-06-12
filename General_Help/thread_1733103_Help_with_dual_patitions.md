---
title: "Help with dual patitions"
date: 2011-04-18
forum: General Help
---

### Post by Stability666 on 2011-04-18
I guess that's what it's called. When I installed ubuntu desktop edition 10.10 i noticed the option for installing it along side windows.. But it looks like it deleted all my ****... Is there any way to get into it?

---

### Post by Quiver on 2011-04-18
What happens when you turn on the computer?

---

### Post by blueridgedog on 2011-04-18
If you are booted into Ubuntu, open a terminal from Applications, Accessories, Terminal, then enter the following command and post the results here:

```
sudo fdisk -l
```

and then

```
mount
```

---

### Post by kiyop on 2011-04-18
How about keeping pressing SHIFT key just after you turn on computer?
If grub menu appears, select Windows or something alike.
If grub menu does not appears, follow [#3]("http://ubuntuforums.org/showthread.php?p=10693014#post10693014")

---

