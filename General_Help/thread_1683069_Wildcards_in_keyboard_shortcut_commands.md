---
title: "Wildcards in keyboard shortcut commands"
date: 2011-02-06
forum: General Help
---

### Post by Taijitu on 2011-02-06
Hello everyone of you delightful people :).

I want to make a keyboard shortcut that runs the following command:

```
smplayer /tmp/Flash*
```

This is to play things as youtube videos etc. in smplayer using vdpau instead of the laggy flashplayer

The wildcard * works in terminals, but not in the command of the shortcut or in the Alt-F2 launcher... Could anyone point me to what I could write instead?

Thanks a lot in advance! :-D

---

### Post by Taijitu on 2011-02-07
Searching for a bit more made me find this answer:

```
bash -c "smplayer /tmp/Flash*"
```

So.. Problem solved :-)

---

