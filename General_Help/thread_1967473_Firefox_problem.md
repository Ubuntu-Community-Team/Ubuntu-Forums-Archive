---
title: "Firefox problem"
date: 2012-04-28
forum: General Help
---

### Post by FemmeFatale on 2012-04-28
Hello, 

I have a strange problem which appears when I open sites like facebook, twitter, some forums, etc. When I try to open a page, there is no text content. What could be the reason for such behaviour?


[[img]http://img6.imageshack.us/img6/4795/screenshotag.png[/img]](http://imageshack.us/photo/my-images/6/screenshotag.png/)

---

### Post by brainwash on 2012-04-28
Can you reproduce this issue when running Firefox in safe mode?
```
firefox -safe-mode
```

---

### Post by FemmeFatale on 2012-04-28
It happens exactly the same in safe mode too.

---

### Post by carl4926 on 2012-04-28
Close ffox
Rename your current .mozilla to .mozilla-bak

Now test it

---

### Post by FemmeFatale on 2012-04-28
ff@amidala ~ $ mv .mozilla/ .mozilla-bak
ff@amidala ~ $ firefox

(firefox.real:7202): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='IndicEngineFc', font='Lucida Grande Medium 14.6669921875', text=' '

still the same.

---

### Post by FemmeFatale on 2012-04-28
Issue resolved. I put my win7 and Mac fonts in /usr/share/fonts/truetype and now looks fine.

---

### Post by carl4926 on 2012-04-28
> **FemmeFatale said:**
> Issue resolved. I put my win7 and Mac fonts in /usr/share/fonts/truetype and now looks fine.
How random is that

---

