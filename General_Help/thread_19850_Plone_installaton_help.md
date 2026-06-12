---
title: "Plone installaton help"
date: 2005-03-14
forum: General Help
---

### Post by Vaquero on 2005-03-14
I am running Hoary and am trying to setup a Plone server.  Apt-get went well with no error message.  Unlike Window installation, it never stops to ask me to setup password and such.  Also, when trying to connect to [http://localhost:9673/manage](http://localhost:9673/manage) will only get a connection refusal,  what did I miss ?

---

### Post by jdodson on 2005-03-14
do not post questions to the how to section.  please check forum area rules before posting.

---

### Post by elwis on 2005-03-14
[QUOTE=Vaquero]I am running Hoary and am trying to setup a Plone server.  Apt-get went well with no error message.  Unlike Window installation, it never stops to ask me to setup password and such.  Also, when trying to connect to [http://localhost:9673/manage](http://localhost:9673/manage) will only get a connection refusal,  what did I miss ?[/QUOTE]

I just did an apt-get of Zope and it doesn't work at all. All I have is an emergency user that can't do nothing! this one will go down the sink for sure - but please tell me if you find out howto.

(you did start the server did you?)

EDIT: I'll correct that - I did Zope to go with some instant hacking and the commandword
sudo zope-zpasswd -e SHA -u admin -p passwd var/lib/zope/instance/default/access

---

