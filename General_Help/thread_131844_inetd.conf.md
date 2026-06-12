---
title: "inetd.conf"
date: 2006-02-17
forum: General Help
---

### Post by biguns on 2006-02-17
I was just reading up on some security "best practices" and one of the suggestions is to stop unneeded services from starting. I looked at my /etc/inetd.conf file and it is empty...

Is that normal?

---

### Post by heimo on 2006-02-17
I think inetd.conf shouldn't be empty after default install, but I'm not sure. However you can run daemons without "super server", so it doesn't really control all the services that might be running. Fortunately, by default Ubuntu doesn't install any outside listening services. That's a very good policy.

---

### Post by biguns on 2006-02-17
I'm not familair with the term "Super Server" but I'll look it up.

Thanks

---

### Post by heimo on 2006-02-17
[inetd]("http://en.wikipedia.org/wiki/Inetd") = super server, it's a [daemon]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29"), which launches other services. It's good for some purposes, but you may also configure services to run without inetd. In that case, the service daemon itself is listening and waiting for new connections.

---

### Post by biguns on 2006-02-17
Thanks for the links to Wikipedia...great source of info...

---

