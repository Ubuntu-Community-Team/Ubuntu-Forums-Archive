---
title: "Sendmail don't send"
date: 2011-02-22
forum: General Help
---

### Post by Sinopa on 2011-02-22
*Sings* It finally happened. I'm going slightly maaaad. :P

So I installed sendmail and I configured php.ini. Then I tried to send an e-mail through a contact form I made, but no dice. It didn't work. No mail was sent and for 2 days now I have been trying to get sendmail to work. 

When I test sendmail with sudo ps aux | grep sendmail I get this reply:

```
root     23776  0.0  0.1  11492  1872 ?        Ss   08:55   0:00 sendmail: MTA: accepting connections          
root     23777  0.0  0.1  11564  2556 ?        S    08:55   0:00 sendmail: MTA: ./p1QAMZeb002698 gmail-smtp-in.l.google.com.: user open
smmsp    23798  0.0  0.0   9532  1416 ?        Ss   08:55   0:00 sendmail: MSP: Queue runner@00:20:00 for /var/spool/mqueue-client
hanna    23975  0.0  0.0   4008   748 pts/0    S+   08:55   0:00 grep --color=auto sendmail

```
It says accepting connections, but why won't it send. And WHAT is Google doing in my sendmail? I tried praying [-o<, but that didn't work. I banged my head against the wall ](*,), but that didn't work either. 

I'm more confused then usual.

---

### Post by Sinopa on 2011-02-25
*bump*

---

### Post by Sinopa on 2011-02-27
*bump*

---

