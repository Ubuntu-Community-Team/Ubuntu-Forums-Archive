---
title: "Running a second instance of Apache as a user"
date: 2009-09-13
forum: General Help
---

### Post by supradave on 2009-09-13
I'm wondering if I can have a second (or third, etc.) instance of Apache running as me, a non-privileged user.  For example, I have the main server running from /var/www, but I would like to be able to start a second instance with a document root of /home/user/tmp/html (or similar).  I can't have a second document root in my /home directory in the the main Apache config because the Apache user doesn't have permission to get into my home directory, which leads me to this dilemma.  I know it would need to run on a different port, so that's not an issue.  Do I just need to create a second apache2.conf in my home?

Thanks,
Dave

---

