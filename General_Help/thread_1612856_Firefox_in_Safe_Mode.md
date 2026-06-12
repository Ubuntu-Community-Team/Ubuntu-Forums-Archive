---
title: "Firefox in Safe Mode?"
date: 2010-11-03
forum: General Help
---

### Post by ArsenalFan2010 on 2010-11-03
Hi, I really need to open Firefox in Safe Mode as I have installed foxyproxy and it's gone wrong!!, and it won't let firefox open, so i need to open it in safe mode, how would i go about doing that? All help will be appreciated greatly!

Thanks

---

### Post by sikander3786 on 2010-11-03
From terminal (Applications > Accessories > Terminal), kill any instances of firefox by

```
ps axjf | grep firefox
```

and then

```
firefox -safe-mode
```

---

