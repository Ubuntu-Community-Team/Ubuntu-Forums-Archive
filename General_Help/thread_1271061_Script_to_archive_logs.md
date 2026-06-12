---
title: "Script to archive logs"
date: 2009-09-20
forum: General Help
---

### Post by christopher_m_bennett on 2009-09-20
I'm looking for a simple script to move and archive logs created by a windows application.  The application starts a new log when it reaches a certain size.  I want to move all logs except the one currently being written to so they can be processed and archived.  I cant suspend the windows app and move all of them so I need a reliable way to identify the one still being written and skip that one.  Any ideas would be helpful

Thanks

---

### Post by denver on 2009-09-20
Is the log on a network share? Please provide some information regarding the setup you are facing.

If the log is saved to a network share to which you have write access to, you could take a look at:

```
logrotate
```

Its in the repositories.

---

