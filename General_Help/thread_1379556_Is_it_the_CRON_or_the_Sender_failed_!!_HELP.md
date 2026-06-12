---
title: "Is it the CRON or the Sender failed !! HELP"
date: 2010-01-12
forum: General Help
---

### Post by baday2003 on 2010-01-12
hello
i thought  i had a  problem with  cron but  now i have a  feeling its the   mailing server or  mailing  the  cron cant  msg to my  E-mail !


I opened this 



```
  GNU nano 2.0.9                           File: /var/log/syslog                                                             

Jan 12 07:40:54 vm54bfredk syslogd 1.5.0#5ubuntu3: restart.
Jan 12 07:40:54 vm54bfredk anacron[28916]: Job `cron.daily' terminated (mailing output)
Jan 12 07:40:54 vm54bfredk postfix/smtpd[19552]: connect from vm54bfredk.zazeen.com.local[127.0.0.1]
Jan 12 07:40:54 vm54bfredk postfix/smtpd[19552]: NOQUEUE: reject: RCPT from vm54bfredk.zazeen.com.local[127.0.0.1]: 504 5.5.$
Jan 12 07:40:54 vm54bfredk postfix/smtpd[19552]: lost connection after RCPT from vm54bfredk.zazeen.com.local[127.0.0.1]
Jan 12 07:40:54 vm54bfredk postfix/smtpd[19552]: disconnect from vm54bfredk.zazeen.com.local[127.0.0.1]
Jan 12 07:40:54 vm54bfredk anacron[28916]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail)$
Jan 12 07:40:54 vm54bfredk anacron[28916]: Normal exit (1 job run)




  GNU nano 2.0.9                           File: /var/log/syslog                                                             

Jan 12 18:20:01 vm54bfredk /USR/SBIN/CRON[19755]: (main) MAIL (mailed 102 bytes of output but got status 0x0001 )
Jan 12 18:21:02 vm54bfredk /USR/SBIN/CRON[19944]: (root) CMD (cd /var/www/virtual/e-suliman.com/htdocs/periodic; /usr/bin/ph$
Jan 12 18:21:02 vm54bfredk /USR/SBIN/CRON[19946]: (main) CMD (cd /var/www/virtual/e-suliman.com/htdocs/periodic; /usr/bin/ph$
Jan 12 18:21:02 vm54bfredk sSMTP[19950]: RCPT TO:<baday2004@hotmail.com> (550 Sender verify failed)
Jan 12 18:21:02 vm54bfredk /USR/SBIN/CRON[19930]: (main) MAIL (mailed 102 bytes of output but got status 0x0001 )
Jan 12 18:22:01 vm54bfredk /USR/SBIN/CRON[20000]: (root) CMD (cd /var/www/virtual/e-suliman.com/htdocs/periodic; /usr/bin/ph$
Jan 12 18:22:01 vm54bfredk /USR/SBIN/CRON[20002]: (main) CMD (cd /var/www/virtual/e-suliman.com/htdocs/periodic; /usr/bin/ph$
Jan 12 18:22:01 vm54bfredk sSMTP[20007]: RCPT TO:<baday2004@hotmail.com> (550 Sender verify failed)
Jan 12 18:22:01 vm54bfredk /USR/SBIN/CRON[19986]: (main) MAIL (mailed 102 bytes of output but got status 0x0001 )
Jan 12 18:23:01 vm54bfredk /USR/SBIN/CRON[20056]: (root) CMD (cd /var/www/virtual/e-suliman.com/htdocs/periodic; /usr/bin/ph$
Jan 12 18:23:01 vm54bfredk /USR/SBIN/CRON[20058]: (main) CMD (cd /var/www/virtual/e-suliman.com/htdocs/periodic; /usr/bin/ph$
Jan 12 18:23:01 vm54bfredk sSMTP[20066]: RCPT TO:<baday2004@hotmail.com> (550 Sender verify failed)
Jan 12 18:23:01 vm54bfredk /USR/SBIN/CRON[20042]: (main) MAIL (mailed 102 bytes of output but got status 0x0001 )


```???

Can any one help me 



(  and  another  Im new  tothis  , and i  tried to install a SMTP SERVER  so i can use it on my PHPBB3 

SMTP server address:    
SMTP server port:
Authentication method for SMTP:
SMTP username:
SMTP password:

Please  show me  how can i do that  2 !!! ) 






thanks

---

### Post by baday2003 on 2010-01-12
echo !!! :(

---

