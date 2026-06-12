---
title: "Something missing for mail to be send"
date: 2012-05-14
forum: General Help
---

### Post by sphairos on 2012-05-14
Hi guys,

I run a ubuntu 10.04 and make a simple bash :

```
#!/bin/bash
# script to send simple email
# email subject
#SUBJECT="Espace des disques durs sur :" $(hostname -f) "du :" $(date +"%d/%m/%Y")
SUBJECT="Espace des disques durs sur "
EMAIL="xxxx@sxxxx.com"
df -h >> /Monitoring/HD_infos_$(date +"%d_%m_%Y").txt
EMAILMESSAGE=/Monitoring/HD_infos_$(date +"%d_%m_%Y").txt
/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
```

to I get no error message at first but when I enter the command "mail" I get the following error message : 
[http://screencast.com/t/lXO4mCTpbaaP]("http://screencast.com/t/lXO4mCTpbaaP")

No firewall is blocking the smtp port from in to out.
I used the command netstat -tap | grep smtp it returned : 
tcp      0      0 localhost:smtp     *:*     LISTEN     4319/master
But to be honnest I don't know what to do with that.

So here I am, hope anybody can help!

Thanks in advance

---

### Post by dcstar on 2012-05-15
> **sphairos said:**
> Hi guys,

I run a ubuntu 10.04 and make a simple bash :

```
#!/bin/bash
# script to send simple email
# email subject
#SUBJECT="Espace des disques durs sur :" $(hostname -f) "du :" $(date +"%d/%m/%Y")
SUBJECT="Espace des disques durs sur "
EMAIL="xxxx@sxxxx.com"
df -h >> /Monitoring/HD_infos_$(date +"%d_%m_%Y").txt
EMAILMESSAGE=/Monitoring/HD_infos_$(date +"%d_%m_%Y").txt
/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
```

to I get no error message at first but when I enter the command "mail" I get the following error message : 
[http://screencast.com/t/lXO4mCTpbaaP]("http://screencast.com/t/lXO4mCTpbaaP")

No firewall is blocking the smtp port from in to out.
I used the command netstat -tap | grep smtp it returned : 
tcp      0      0 localhost:smtp     *:*     LISTEN     4319/master
But to be honnest I don't know what to do with that.

So here I am, hope anybody can help!

Thanks in advance

Install **postfix**.

---

