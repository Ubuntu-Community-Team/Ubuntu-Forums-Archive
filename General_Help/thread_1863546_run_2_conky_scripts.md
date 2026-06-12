---
title: "run 2 conky scripts"
date: 2011-10-17
forum: General Help
---

### Post by l3ecl on 2011-10-17
As the title suggests, I have two conky scripts but whenever I run them together, it comes out like a 3 yr old slapped food onto a wall.

Individually they run fine, but when I run them together, conky hates me.

What should be the approach here? 

1. I tried combining the two scripts into 1 but it dosen't come out right.

2. I've also tried running them, separately, both at the same time, and it doesn't come out right:

```
conky -c /home/jk/.conky/script1 /home/jk/.conky/script2
```

My two conky scripts can be found here below.

This is my main conky script:
[http://pastebin.com/tJTAUm67](http://pastebin.com/tJTAUm67)

This is my conky script to run google calendar in my desktop
[http://pastebin.com/nGhV6ubd](http://pastebin.com/nGhV6ubd)

Help is much appreciated

---

### Post by TeoBigusGeekus on 2011-10-18
Try running them with
```
conky -c /home/jk/.conky/script1 [COLOR="Red"]-c[/COLOR] /home/jk/.conky/script2
```

---

### Post by l3ecl on 2011-10-18
Thanks!

I could have just googled that.

---

