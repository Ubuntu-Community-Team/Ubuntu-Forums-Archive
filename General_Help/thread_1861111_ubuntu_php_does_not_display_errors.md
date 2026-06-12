---
title: "ubuntu php does not display errors"
date: 2011-10-15
forum: General Help
---

### Post by Andreei on 2011-10-15
I installed php5 apache2 and mysql on ubuntu and they all work but they don't display any php errors.I edited my php.ini file to display_errors = On what else should i do (i already googled the topic)

---

### Post by SeijiSensei on 2011-10-15
All the errors are logged to /var/log/apache2/error.log.  That's a security precaution.  Displaying PHP errors on the web page itself can provide potential hackers with useful information to exploit your site.

---

### Post by Andreei on 2011-10-16
i know that but this is only for localhost testing and debugging

---

