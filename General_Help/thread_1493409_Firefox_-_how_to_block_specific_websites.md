---
title: "Firefox - how to block specific websites?"
date: 2010-05-25
forum: General Help
---

### Post by danbuter on 2010-05-25
Is there an add-on for Firefox where I can have it block specific websites? I don't need the full no-adult block which often block stuff that really isn't all that adult, but something where I can just add in the URL and it will never show up again. Thanks!

---

### Post by lisati on 2010-05-25
I haven't tried it, but you might want to check out [BlockSite]("https://addons.mozilla.org/en-US/firefox/addon/3145/")

---

### Post by danbuter on 2010-05-25
thanks!

---

### Post by wojox on 2010-05-25
You could always do it manually. Open a terminal:

```
gksudo gedit /etc/hosts
```

And add:

```

0.0.0.0 www.myspace.com
0.0.0.0 www.facebook.com

```

Restart, and this would block Facebook and MySpace from any browser.

---

### Post by WorMzy on 2010-05-25
You can edit /etc/hosts so that any unwanted websites redirect to 127.0.0.1

e.g. adding:
```
127.0.0.1	www.excite.com
```
to /etc/hosts makes firefox (and any other browser) redirect to 127.0.0.1 (localhost) whenever someone tries to visit [www.excite.com](www.excite.com)


Edit: Beaten.

---

### Post by sille777 on 2010-05-25
could i use the same idea and redirect a blocked site to lets say google?

by replacing the 0.0.0.0 or 127.0.0.1 with [www.google.com?]("http://www.google.com?")

---

### Post by WorMzy on 2010-05-25
In a way, yes. The first value has to be an IP address, not a domain name, so if you find the IP address of your nearest google server (use nslookup in a terminal), and use that, then it'll redirect you to google.

e.g. my closest google server is located at 66.102.9.105 so if I edit my hosts file to say: ```
66.102.9.105	www.excite.com
``` going to [www.excite.com](www.excite.com) will redirect me to google.

---

