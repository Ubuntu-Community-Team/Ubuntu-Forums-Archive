---
title: "which tutorial should I follow"
date: 2012-03-19
forum: General Help
---

### Post by drfoo on 2012-03-19
Greetings

Ive setup 2 ubuntu 11 servers. there are SO many tutorials and guides out there I don't know which one to follow or use as a reference. some are setup for ubuntu 6 some for 8 some for squeeze some for your knees
Can someone guide me to the best setup tutorial for 
POSTFIX SASL TLS DOVECOT

i have two installs both came up with different info in their setups. I need to drop back and set these two systems the same, but I need the most current setup. not something written in 2007.

two lines that made me scratch my head and wonder " where did that come from ",...

first system:
```
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_type = dovecot

```

second system:
```
mailbox_command = procmail -a "$EXTENSION"
```


Im assuming the first system is correct, I wanted to look at a current tutorial or setup guide and check. thanks

---

### Post by Bucky Ball on 2012-03-19
Can't help with your issue but just a word: LTS releases recommended for servers (five years support and stable). 10.04 LTS current (support until April 2015) and 12.04 LTS out in late April this year, although I'd wait a couple of months before upgrading. LTS intended for production machines and servers. ;)

---

### Post by TuxVinyards on 2012-04-01
The 'procmail' bit is something else.  I'm currently using procmail with my old server. It has some really effective regex filters systems. Recommended.

Try here - 

[http://www.ii.com/internet/robots/procmail/qs/#etcProcmailrc](http://www.ii.com/internet/robots/procmail/qs/#etcProcmailrc)

[http://perlcode.org/tutorials/procmail/proctut/](http://perlcode.org/tutorials/procmail/proctut/)

[http://lipas.uwasa.fi/~ts/info/proctips.html](http://lipas.uwasa.fi/~ts/info/proctips.html)

[http://partmaps.org/era/procmail/links.html](http://partmaps.org/era/procmail/links.html)

I really sympathise with you on the tutorial / doc front.  It's even more annoying when people don't even date what they writing. But at least there has been something written. Trying to keep pace with changes is very difficult. If you have found something during the last week, here is your opportunity for a community contribution .....

I am currently setting up a new server, this time dedicated virtual, with full root control. I have gone for the Ubuntu 'mail-stack-delivery' package as it seems to be straight forward.

Can't say detailing on the subtle relationship between Dovecot and Postfix is too good but the package seems to be generally what I am looking for, so far. It's a fairly standard solution and much the same as I have  been using, plus I can actually get to access the conf files this time.

---

### Post by 2F4U on 2012-04-01
Did you check the Ubuntu server documentation? It is available for every version out there and I would always prefer that over any other unless it doesn't contain what you need.

[https://help.ubuntu.com/11.04/serverguide/C/postfix.html](https://help.ubuntu.com/11.04/serverguide/C/postfix.html)
[https://help.ubuntu.com/11.10/serverguide/C/postfix.html](https://help.ubuntu.com/11.10/serverguide/C/postfix.html)

Another good reference would be the community documentation about postfix:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

