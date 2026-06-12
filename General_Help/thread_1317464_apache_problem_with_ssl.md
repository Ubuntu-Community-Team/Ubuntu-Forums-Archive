---
title: "apache problem with ssl"
date: 2009-11-06
forum: General Help
---

### Post by supradave on 2009-11-06
I have a personal webserver with a self-signed ssl cert.  When I type in my domain, [http://www.webserver.com](http://www.webserver.com), I have it Redirect permanent to [https://www.webserver.com](https://www.webserver.com).  If I type in type in something like [http://www.webserver.com/nextpart](http://www.webserver.com/nextpart), I will get a server not found error and my URL (in Firefox) will look like [https://www.webserver.comnextpart/](https://www.webserver.comnextpart/).  This will happen whether nextpart exists or not.  I can then go put the slash in the appropriate location and it works fine.

Any ideas why the slash / is getting truncated?

Thanks,
Dave

---

### Post by dvlchd3 on 2009-11-06
set the redirect to [https://www.webserver.com/](https://www.webserver.com/) (with the slash)

---

### Post by supradave on 2009-11-09
No, that's not it.  Still the same behavior.

---

