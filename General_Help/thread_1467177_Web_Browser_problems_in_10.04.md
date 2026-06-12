---
title: "Web Browser problems in 10.04"
date: 2010-04-30
forum: General Help
---

### Post by xrecar on 2010-04-30
Hey guys, this is a bit of a bummer. I recently did a clean install of 10.04 and everything seemed ok and working until I opened one site I like to visit.

I noticed that firefox did not render the page right, so I reloaded. Same thing. Then went to check other sites and the same problem occurs. However, it's not only on firefox, it alos happens on midori.

Here's a screenshot: In this particular one, the titles for the post won't load.
[img]http://img411.imageshack.us/img411/79/screenshot1fm.png[/img]

I've already re-installed firefox, openjdk, the icedtea web browser plugin, flash player and even the ubuntu restricted extras.

I would really appreciate your help.
Thanks in advance.

**Update: ** I solved the problem on both browsers by deleting some fonts I had installed manually.

---

### Post by mikewhatever on 2010-04-30
Are you running any add-ons?
Try closing firefox, and then relaunching it with the following command, any difference?

```
firefox -safe-mode http://www.engadget.com/
```

---

### Post by xrecar on 2010-04-30
Thanks! However, the problem is still there. It also happens on Midori.

---

### Post by xrecar on 2010-05-01
Update: It does not happen on Opera.

---

