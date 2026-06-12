---
title: "pdf2djvu problems"
date: 2010-05-16
forum: General Help
---

### Post by ronlayt on 2010-05-16
Am I missing something? I read all the posts about pdf2djvu and heres the problem. I enter the code like this

code:
pdf2djvu -oSmith-Airplanes.djvu -vSmith-Airplanes.pdf

Now, when I enter I get the "too many arguments" message and no djvu document. Is there a rule about capitol letters,dash's,etc? I have many pdf doc's taking up too much space and I prefer djvu doc's. Thanks all!

---

### Post by Rytron on 2010-07-21
Hello ronlayt.

Try:
```
pdf2djvu -o Smith-Airplanes.djvu Smith-Airplanes.pdf -v
```

---

