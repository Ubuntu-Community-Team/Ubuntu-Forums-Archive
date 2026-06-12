---
title: "PHP Issue"
date: 2010-02-23
forum: General Help
---

### Post by daniel50096230 on 2010-02-23
I have the following issue in my php web app:

iemsERP Login screen
**Warning**: session_start() [[function.session-start]("http://ubuntuforums.org/function.session-start")]:  open(/var/lib/php5/sess_fcee43e1645889b03da56025cd871adf, O_RDWR) failed:  Permission denied (13) in **/var/www/iemsERP/includes/session.inc** on line  **23**

**Warning**: session_start() [[function.session-start]("http://ubuntuforums.org/function.session-start")]: Cannot send session  cookie - headers already sent by (output started at  /var/www/iemsERP/includes/session.inc:23) in  **/var/www/iemsERP/includes/session.inc** on line  **23**

**Warning**: session_start() [[function.session-start]("http://ubuntuforums.org/function.session-start")]: Cannot send session  cache limiter - headers already sent (output started at  /var/www/iemsERP/includes/session.inc:23) in  **/var/www/iemsERP/includes/session.inc** on line **23**


anyone know what is the problem of it and how to resolve this problem?

---

