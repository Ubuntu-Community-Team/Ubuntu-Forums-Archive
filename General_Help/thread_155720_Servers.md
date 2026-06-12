---
title: "Servers"
date: 2006-04-05
forum: General Help
---

### Post by kevieboy on 2006-04-05
I'm running an Intel machine and am looking to set up a ftp and appleshare server.  Does anyone know how to do this?

---

### Post by David Corrales on 2006-04-05
About the FTP server, you should install the package called **proftpd** which is a good ftp server. Just type **sudo apt-get install proftpd**.
It's configured in a way similar to Apache 2. As a tip, unless you need reverse dns resolution, you should use the directive *UseReverseDNS   off* to speed up the login of clients.

---

### Post by kevieboy on 2006-04-05
Thanks. It works like a charm.  Now only for the Appletalk server...

---

### Post by kevieboy on 2006-04-09
How do you configure the shared directories for proftpd?

---

