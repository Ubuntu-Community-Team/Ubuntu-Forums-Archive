---
title: "wget will only download index.html"
date: 2012-02-29
forum: General Help
---

### Post by CrusaderAD on 2012-02-29
```
wget -A "*.pdf" http://www.123.com/test/
```

Will only download an index.html file and none of the pdf files. The directory is fully browsable. Any help?

---

### Post by musicman10489 on 2012-02-29
I just tried the command you posted and returned a '404 Not Found'. Are you sure it's still active?

---

### Post by CrusaderAD on 2012-02-29
> **musicman10489 said:**
> I just tried the command you posted and returned a '404 Not Found'. Are you sure it's still active?

That was a test site, not a true url. I can't post that.

---

### Post by Khayyam on 2012-02-29
The syntax (-A) is correct, but there probably isn't a pdf on webroot/ .. your should also probably use '-r' (--recursive).

HTH ... khay

---

