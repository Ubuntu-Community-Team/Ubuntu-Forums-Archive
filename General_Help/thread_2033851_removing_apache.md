---
title: "removing apache"
date: 2012-07-27
forum: General Help
---

### Post by mich3lam on 2012-07-27
Well, a while ago I tried installing Apache to a localhost server and it made me a page at 127.0.0.1. Now I removed Apache by using those commands:
```
sudo apt-get remove apache2
sudo apt-get autoremove
```
But still when I visit 127.0.0.1 I have that page saying:
[HTML]**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.
[/HTML]
Doesn't that mean it isn't completely removed? how can I fix that? thank you@

---

### Post by albandy on 2012-07-27
type this:
```
dpkg --get-selections | grep apache
```

then post the answer.

---

