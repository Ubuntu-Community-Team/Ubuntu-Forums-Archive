---
title: "khtml2png problem in VPS"
date: 2011-10-26
forum: General Help
---

### Post by ask995 on 2011-10-26
I am trying to install khtml2png on my Linode VPS (Ubuntu 10.04). Followed this guide [http://bit.ly/tssWYK](http://bit.ly/tssWYK)

Everything installed smoothly.

Now I am facing this error when trying to generate screenshot.

```
khtml2png2 http://facebook.com facebook.png
kbuildsycoca running...
DCOP Cleaning up dead connections.
terminate called after throwing an instance of 'DOM::DOMException'
KCrash: Application 'khtml2png2' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
root@ask995:/srv/www/<sitename>/public_html/screenshots# DCOP aborting call from 'anonymous-23641' to 'kded'
```

Can anyone help me out with it? Any hint you are getting from above erros.

**PS:** I am on 512 MB Linode VPS.

---

