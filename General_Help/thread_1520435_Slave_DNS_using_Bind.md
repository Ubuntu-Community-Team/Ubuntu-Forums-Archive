---
title: "Slave DNS using Bind"
date: 2010-06-29
forum: General Help
---

### Post by ajarduini on 2010-06-29
Greetings everyone. Before I start, please know I am new to the ubuntu and bind dns field.

 I am trying to configure a bind slave dns server.  I have been following the instructions on [https://help.ubuntu.com/community/BIND9ServerHowto#Secondary%20Master%20Server%20configuration](https://help.ubuntu.com/community/BIND9ServerHowto#Secondary%20Master%20Server%20configuration) under the section of how to configure a Secondary Master Server configuration.  From what I can tell my files are okay, but I am running into the following error when restarting the bind services on my server.  

Stopping domain name service... bind 9 [OK]
rndc: connect failed: 127.0.0.1#953: connection refused.

From my understand when I restart the service it should sync with my master server, but I am getting this error.

I have a few questions in my head about this.  I just configured the named.conf.local for my zone and reverse zone as the website above tells me.  I have a feeling that I have to do more then that with a fresh install.

Do I have to configure my zone files manually for the first time?

I am seeing a lot of documentation on this, but nothing that seems to be explaining a fresh install.  It is becoming very confusing.

  I would appreciate any help you can provide me with on this.

---

### Post by ajarduini on 2010-06-30
I've been doing more research and everything I find is supporting what I have done.  That setup seems to easy, something has to be missing right?

Thank you,

Tony

---

