---
title: "wget earth image problem"
date: 2010-11-17
forum: General Help
---

### Post by cnbiz850 on 2010-11-17
I have been using "wget -r -N http://static.die.net/earth/mercator/1600.jpg" to get a rotating earth's image and setting it as background.  But since yesterday, the file downloaded is wrong - the size is only 37 bytes.  However, Firefox can download the right file.  Anyone know what is the problem?

---

### Post by Ancanus on 2010-11-17
Perhaps they are blocking wget?

Try

```

wget -U Mozilla/5.0 http://static.die.net/earth/mercator/1600.jpg

```

---

### Post by cnbiz850 on 2010-11-17
Thanks so much.  That works.

---

### Post by draki on 2010-11-18
That worked for me too - many thanks!

---

