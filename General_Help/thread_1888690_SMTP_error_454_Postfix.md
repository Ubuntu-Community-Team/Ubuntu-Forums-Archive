---
title: "SMTP error 454 Postfix"
date: 2011-11-29
forum: General Help
---

### Post by streetlightman on 2011-11-29
Hello,

So I am working on a school project where it is my job to set up a Collaboration server.  I chose to go with Synovel Collabsuite.  Looking back on that decision, I might have chosen something else since no one seems to be using this.

Regardless, I'm working on setting up email.  I do not have a website so I am using a fake FDQN.  When I go to send email to myself on the server I get an smtp 454 error.  I assume this has something to do with the TLS security that comes pre-setup on the installation CD.

My question is, how do I completely disable security on the SMTP server.  It is a Postfix SMTP server running.

Thanks!

---

### Post by galvatron408 on 2011-11-30
454 error just means that you don't have permission to send messages to that server.

Your assumption is wrong, because it is not TLS. 

Here is what you need to do.
[http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from](http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from)

---

