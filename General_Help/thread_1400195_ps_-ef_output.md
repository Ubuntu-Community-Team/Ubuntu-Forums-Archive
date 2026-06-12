---
title: "ps -ef output"
date: 2010-02-06
forum: General Help
---

### Post by mmaru on 2010-02-06
$ps -ef

Under the TTY column, what does a ? mean.

Regards,

-Maru

---

### Post by s.fox on 2010-02-06
Hello,

Those are not attached to any particular terminal. This is most common with daemons, which are processes which run without attaching to any particular terminal. Common daemons are sendmail, BIND, apache, and NFS. They typically listen for some request from a client, and return information to it upon request.

Information sourced from [here]("http://www.slackbook.org/html/process-control-ps.html")

-Silver Fox

---

### Post by mmaru on 2010-02-06
Thank you. It makes perfect sense.

---

