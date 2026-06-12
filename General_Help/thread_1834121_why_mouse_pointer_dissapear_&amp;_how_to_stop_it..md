---
title: "why mouse pointer dissapear &amp; how to stop it."
date: 2011-08-27
forum: General Help
---

### Post by vikash_chandola on 2011-08-27
Why sometimes pointer in Ubuntu disappear after some time. Some times instantly. let me explain. Today i try libre office draw , when i was making diagram mouse pointer instantly disappear as i stop moving mouse. as i move it, it comes back. It creates problem in drawing. Finally i need to go windows and draw in paint.
Can you tell me how to change mouse setting so that it doesn't disappear in any condition.

---

### Post by WyleECoyote on 2011-08-27
you may have "unclutter" install check using this command:
```
which unclutter
```

if that shows anything then run this:
```
killall unclutter
```

there is no nice way of stopping it, and if you never want to use it again you can just remove it:
```
sudo apt-get remove unclutter
```

---

