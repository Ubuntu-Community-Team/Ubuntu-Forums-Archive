---
title: "How to change privileges for negative nice values -- I want to do it as regular user"
date: 2010-01-16
forum: General Help
---

### Post by thekronisk on 2010-01-16
Hi.

I've been searching for the answer to my question for quite some time on google, no luck.
Due to my searchings I've become very familiar with nice and renice.

I have a script I use for launching a game installed with wine. I cannot/wont run this game as root but I need to be able to use nice --7. As of now I can't I -- ofc -- get "permission denied".. 

So how do I make the full range of niceness ( [-19;20] IIRC ) available for all users on my system -- or even just for 1 user?

Thanks in advance

---

### Post by kidders on 2010-01-17
Hi there,

> **thekronisk said:**
> So how do I make the full range of niceness ( [-19;20] IIRC ) available for all users on my system -- or even just for 1 user?

Afaik you can't, because it would give unprivileged users too much influence over the stability of your box. One way of achieving the same effect is to launch your game as yourself, and renice it as root afterwards. For instance ...

```
#!/bin/bash
sleep 10 &
[ $? -eq 0 ] && sudo renice -7 $!
```

The "sleep" command is just a dummy, for the sake of example ... you'd replace it with whatever you need to execute to start your game. For convenience, you could also modify /etc/sudoers to allow you to run renice as root without a password. That way, the script would be non-interactive.

I hope that helps.

---

