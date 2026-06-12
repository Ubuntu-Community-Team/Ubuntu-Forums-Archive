---
title: "Problems sending mails from Ubuntu"
date: 2011-09-15
forum: General Help
---

### Post by jlabuelo on 2011-09-15
Hi all

We had alfresco 3.0 ECM running on a windows machine and everything worked fine. We are trying to move the configuration we have to Linux Ubuntu now, and also 95% of the functionalities are working fine, however we have a problem with the mails sent by the server.

In some actions of the application it must send a mail to the users, but with Ubuntu 8.0.4 in Amazon EC2 (where the server is located now)  mails are sent with strange characters, the header does not content the subject or mail origin....

This is the header that the code produces but is not appearing when the mail arrives to destination: (works fine with the application running in Windows).
> From: [EMAIL="soporte@simplysmart.es"]soporte@simplysmart.es[/EMAIL] To: [EMAIL="agey@simplysmart.es"]agey@simplysmart.es[/EMAIL] Subject: Factura emitida por Simply Smart MIME-Version: 1.0 Content-Type: text/html;charset=UTF-8 Content-Transfer-Encoding: quoted-printable
the body of the email appears in "plain text" and I think it is not taking in account the "Content-Transfer-Enconding".
The configuration worked fine in Windows, but do not know what can be the error that is producing this behaviour 
now that we try to move the code to Ubuntu.

Any ideas about what to start looking at??? Does anyone got this kind of 
erros anytime before??

Regards.

---

### Post by Bobrm2 on 2011-09-15
I'm Ubuntu 10.10, and latest Evolution. My outgoing mail is also being held in my "out" box. No solution and seeking help also.

Bob

---

