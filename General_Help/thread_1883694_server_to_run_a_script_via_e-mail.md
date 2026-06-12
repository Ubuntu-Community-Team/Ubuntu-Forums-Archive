---
title: "server to run a script via e-mail"
date: 2011-11-19
forum: General Help
---

### Post by sparky-steve on 2011-11-19
Hello,

I'm running ubuntu server 10.04.3 LTS. Headless and no X.

I'd like to be able to e-mail my server, and it run one of a few scripts, depending on the content of the e-mail.

The email would not contain any commands in as far as running the contents of the e-mail, but the e-mail would have a keyword, which will tell the server which script to run.

It would not be necessary to run as root. The server does not host the mail, so it would need to collect the e-mail via pop3.

Any pointers gratefully received.

SS

---

### Post by azmyth on 2011-11-19
Promail will do what you want to do.

[http://www.procmail.org/](http://www.procmail.org/)

---

### Post by gordintoronto on 2011-11-19
Procmail is also in the repositories.

My son set up his office so that a user, at home, could send email to the office, and VNC server would start up on his or her computer. When the user is finished, he or she shuts down the VNC server. This limits the potential security exposure.

---

### Post by sparky-steve on 2011-11-21
Thanks for the replies so far....

I'm going to look into Procmail, but does anyone know if it would be able to collect mail from a pop3 account, and process that, or would it rely on it being a "proper" mail server, and mail being delivered to it?

Cheers
SS

---

### Post by SeijiSensei on 2011-11-21
> **sparky-steve said:**
> I'm going to look into Procmail, but does anyone know if it would be able to collect mail from a pop3 account, and process that, or would it rely on it being a "proper" mail server, and mail being delivered to it?

[http://www.fetchmail.info/](http://www.fetchmail.info/)

Fetchmail is in the repositories as well.

---

