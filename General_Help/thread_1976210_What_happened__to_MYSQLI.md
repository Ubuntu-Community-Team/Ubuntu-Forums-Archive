---
title: "What happened  to MYSQLI?"
date: 2012-05-08
forum: General Help
---

### Post by TorMike on 2012-05-08
Upgraded to Server 12, installed php/apache2/mysql.  Now I'm missing the mysqli extension.  I can't find it in the php.ini nor the apache2 config.

AND, running phpinfo() against the built there is no mysql or mysqli environment variables listed.  WHAT??

Has anyone run into this problem.  My php is written using mysqli extension, my clients are a waiting???

Help Please.

---

### Post by TorMike on 2012-05-09
Found the problem.

During LAMP I missed php5-mysql.

Here's what I did:

**sudo apt-get install php5 libapache2-mod-****php5** ***[COLOR=Red]php5[/COLOR]***[I]**[COLOR=Red]-mysql [/COLOR]**[COLOR=Red][COLOR=Black]<- missed this guy Duh!

[/COLOR][/COLOR][/I]Might what to keep that in mind

---

