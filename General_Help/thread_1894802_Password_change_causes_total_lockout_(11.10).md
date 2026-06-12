---
title: "Password change causes total lockout (11.10)"
date: 2011-12-13
forum: General Help
---

### Post by durruti36 on 2011-12-13
Hello all,

At the weekend I wanted to change my password as I'd had to disclose it to a colleague. Having been unable to do so in the GUI, I ran passwd %username% in the terminal, put in the password twice on request (it was very slow in asking), then the computer crashed, no cursor, no mouse, no <Ctrl><Alt><F1>. Nada. 

After reboot I was able to login and change the password , but the machine would not let me sudo. This morning, the login screen accepts my password but then after a few seconds returns me to the login screen.

When I boot into recovery and try to change the password I get 'authentication token manipulation error – password not changed’. I am the computer’s primary/only user and my home directory is encrypted, but my last full backup is over a month old (stupid I know) and most worryingly I took minutes at an important AGM meeting which are not yet distributed.

The details in my /etc/passwd and /etc/shadow are distinct but I’ve been warned against manually editing these. Is there any thing I can do or do I need to reconvene the AGM? :oops:
Yours hopefully,
Matt

---

### Post by durruti36 on 2011-12-14
No-one has any suggestions? Have I really lost all my data?:(
Any suggestions at all very welcome!
Thanks,
Matt

---

