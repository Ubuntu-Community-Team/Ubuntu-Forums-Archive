---
title: "Mail not incoming from external"
date: 2011-03-04
forum: General Help
---

### Post by cronick on 2011-03-04
Hello,

I am setting up a server that is to serve websites and host mail.

I have run into a problem regarding the mail server. The server is completely set up but for some reason it is not receiving the e-mails I am trying to send to it. When i mail to the associated mail address from internal by the "mail" command it works fine. But when I try from an external mail server, the mail never gets through. And I do not receive a bounce e-mail.

It says that the port 25 IS open for TCP connections (in iptables - I opened it myself). And surely when I telnet to it on that port from inside the server, I get an connection. But when I telnet from an external network I get a refused connection. 

It would sound that the port is in fact not really open for external use, in my mind, but it is. Is there possibly anything else I might have neglected to check in this mystery?

Regards

---

### Post by cronick on 2011-03-04
I solved my problem.

Apparently it was sendmail that was not accepting connections from outside the local network.

---

