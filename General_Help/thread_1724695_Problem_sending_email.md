---
title: "Problem sending email"
date: 2011-04-08
forum: General Help
---

### Post by vivek.pandey on 2011-04-08
HEY EVERYONE
     i am using this python code to send an email 
```
 
#!/usr/bin/python

import smtplib

sender = 'from@fromdomain.com'
receivers = ['to@todomain.com']

message = """From: From Person <from@fromdomain.com>
To: To Person <to@todomain.com>
Subject: SMTP e-mail test

This is a test e-mail message.
"""

try:
   smtpObj = smtplib.SMTP('localhost')
   smtpObj.sendmail(sender, receivers, message)         
   print "Successfully sent email"
except SMTPException:
   print "Error: unable to send email"

```
but when i try to run this code i am getting following error
```


vivek@NEO:~$ python email.py
Traceback (most recent call last):
  File "email.py", line 3, in <module>
    import smtplib
  File "/usr/lib/python2.6/smtplib.py", line 46, in <module>
    import email.utils
  File "/home/vivek/email.py", line 21, in <module>
    except SMTPException:
NameError: name 'SMTPException' is not defined

```

then i typed only this
```

>>> import smtplib

```
and i got this error
```


Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/smtplib.py", line 46, in <module>
    import email.utils
  File "email.py", line 21, in <module>
    except SMTPException:
NameError: name 'SMTPException' is not defined

```
apparently there is something wrong with /usr/lib/python2.6/smtplib.py but i cant make it out
can anyone please help me out
thank you all

---

### Post by vivek.pandey on 2011-04-09
anyone please

---

### Post by vivek.pandey on 2011-04-10
bump

---

