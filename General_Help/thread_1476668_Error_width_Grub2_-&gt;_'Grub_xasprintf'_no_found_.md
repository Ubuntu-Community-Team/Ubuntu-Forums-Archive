---
title: "Error width Grub2 -&gt; 'Grub_xasprintf' no found - Critical issue"
date: 2010-05-08
forum: General Help
---

### Post by JoZ3 on 2010-05-08
Hi, I have installed Ubuntu 10.04 (new installation), has worked perfectly all week, but now back home and turn on the pc I get the following error:
```

Error: the symbol 'Grub_xasprintf' not found
Entering rescue mode ...

```
Actually I have no idea what to do, I reinstalled the GRUB2 and I can not correct the problem. Someone can help me, I need my PC to work

Please seriously that I'm desperate :frown:

Grettings from Colombia

---

### Post by JoZ3 on 2010-05-08
bump!

---

### Post by dino99 on 2010-05-08
just seen your post,

i'm using grub-pc 1.98-1ubuntu6, what is yours ?

as i understand its related to your "locale" es-co special signs with grub, recently have you had some language packages updates ?

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/537998](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/537998)

in case of downgrading, add this ppa to synaptic repo: [COLOR="Blue"]ppa:bugs-da/grub-choose-default[/COLOR] and "force" the ubuntu5 version.

---

