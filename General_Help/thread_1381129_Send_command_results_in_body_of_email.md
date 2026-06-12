---
title: "Send command results in body of email"
date: 2010-01-14
forum: General Help
---

### Post by hidoa on 2010-01-14
I want to execute a command, then I want to send the results of the command in a plain text email using 'sendEmail'.
 
I was thinking I could pipe the results to a text file, but then I would have to attach the file instead of putting it in the body....
 
I was going to put this in a script and have a cron job execute it daily.

---

### Post by falconindy on 2010-01-14
A mail daemon like postfix will do this for you. Any output from the cronjob will be mailed to the owner of the job.

---

### Post by slakkie on 2010-01-14
echo "this is an email" | mail -s "test email" [email]user@domain.tld[/email]

---

### Post by falconindy on 2010-01-14
> **slakkie said:**
> echo "this is an email" | mail -s "test email" [email]user@domain.tld[/email]
You'll need an MTA like courier to forward mail outside your system.

---

### Post by kaibob on 2010-04-11
This is a 4-month-old thread, but I encountered the same issue and thought I would post an answer in case another forum member encounters this thread. 

One solution is to redirect the output of the command to a text file and to then add the following option to the sendEmail command:

```
-o message-file=file
```

A second option is to use command substitution or similar to create a variable, which can then be placed in the sendEmail command:

```
-m "$var"
```

To give a working example of the latter (but with fictitious email data):

```
#!/bin/bash

msg=$(ls)

sendEmail \
-f kaibob@fictitous.com \
-t recipient@fictitous.com \
-u "Email subject" \
-m "$msg" \
-s outgoing.fictitous.com \
-xu kaibob \
-xp password \
-l email.log
```

As an aside, the version of sendEmail included in jaunty doesn't work. There is a fix or an updated version can be downloaded. 

[http://ubuntuforums.org/showthread.php?t=1448693](http://ubuntuforums.org/showthread.php?t=1448693)

---

