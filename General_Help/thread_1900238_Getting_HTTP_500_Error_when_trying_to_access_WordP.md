---
title: "Getting HTTP 500 Error when trying to access WordPress site"
date: 2011-12-25
forum: General Help
---

### Post by houmank on 2011-12-25
Hi,

When I go to my [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)

I get a success message from Apache2:

```
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
```

I have installed WordPress under /var/www/
But when I try to access it I get a HTTP 500 error message.

What have I missed?

Many Thanks,
Houman

---

### Post by houmank on 2011-12-25
I found the problem in the log file. It was a typo in the wp-config.php

---

