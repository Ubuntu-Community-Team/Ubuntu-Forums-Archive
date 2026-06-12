---
title: "notify-send timeout not working"
date: 2012-10-13
forum: General Help
---

### Post by joecron on 2012-10-13
I am running notify-send, but no matter what setting I give -t, which is the time in milliseconds that the popup should remain on the screen, it lasts for 10 seconds, no more, no less.

I am running ubuntu 12.04, but when I ran the same script on mint maya the -t parameter worked.

Any idea what might be wrong?

---

### Post by pqwoerituytrueiwoq on 2012-10-13
it i use less than 800 for -t it last forever, that said every other number works, but i am using version 0.7.5 in 12.10
```
notify-send -t 700 notify-osd "`notify-send -v`"
```

---

