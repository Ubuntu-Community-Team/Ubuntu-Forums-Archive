---
title: "How to start/stop/access built-in mailserver? Settings for mail clients?"
date: 2010-10-03
forum: General Help
---

### Post by pstein on 2010-10-03
As far as I know there must be a built-in mail server in Ubuntu.
This mail server is used e.g. when a cronjob sends email notifications to certain users.

How can I detect if mail server is currently running?

How can I start/stop this mail server?

Assume I install a new mail client like mailx or Thunderbird: Which mail server address + parameters should I use? 

Thank you
Peter

---

### Post by dcstar on 2010-10-03
> **pstein said:**
> As far as I know there must be a built-in mail server in Ubuntu.
This mail server is used e.g. when a cronjob sends email notifications to certain users.

How can I detect if mail server is currently running?

How can I start/stop this mail server?

Assume I install a new mail client like mailx or Thunderbird: Which mail server address + parameters should I use? 

Thank you
Peter

Install the **postfix** package and you can access it by the localhost address on the server.

---

