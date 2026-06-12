---
title: "mail command not working in terminal &amp; crontab from root"
date: 2009-11-28
forum: General Help
---

### Post by cross157 on 2009-11-28
I'm stumped. I'm getting very weird results from the mail command in terminal.

Case #1 from the **user** prompt:
```
cross157@ubuntu:~$ sudo /usr/bin/mail -s Test name@gmail.com < /home/cross157/Desktop/helloWorld.sh
```

Result #1: successful email to [email]name@gmail.com[/email]

Case #2 from the **user** prompt:
```
cross157@ubuntu:~$ /usr/bin/mail -s Test name@gmail.com < /home/cross157/Desktop/helloWorld.sh
```

Result #2: ```
send-mail: account default not found: no configuration file available
Can't send mail: sendmail process failed 
```

Case #3 from the **root** prompt:
```
root@ubuntu:/# /usr/bin/mail -s Test name@gmail.com < /home/cross157/Desktop/helloWorld.sh
```

Result #3: Failed email, if I open Mutt under the **user** I get this:
From: Mail Delivery System <MAILER-DAEMON@gmail.com>
To: [email]root@gmail.com[/email]
Subject: Undelivered Mail Returned to Sender

I have a root crontab setup that is failing in the same manner. I don't get it, why would *sudo mail* work from the user but *mail* from the root not work?

---

### Post by cross157 on 2009-11-29
I did some more investigating and I think it comes down to environmental variables but I'm too much of an amateur to know how to fix it.

In the above example if I access root with *sudo su* or *sudo -i*. The mail command fails, but if I use *sudo -s* the mail command is successful. Any help would be greatly appreciated. Thanks.

---

### Post by dcstar on 2009-11-29
> **cross157 said:**
> I did some more investigating and I think it comes down to environmental variables but I'm too much of an amateur to know how to fix it.

In the above example if I access root with *sudo su* or *sudo -i*. The mail command fails, but if I use *sudo -s* the mail command is successful. Any help would be greatly appreciated. Thanks.
Do this at your user level and it should create any required files, then try to send again:

```
mail
```

---

### Post by cross157 on 2009-11-29
Thank you for the reply, I tried *mail* command alone and here was the result:

```
cross157@ubuntu:~$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/spool/mail/cross157": 1 message 1 new
>N  1 MAILER-DAEMON@gma  Sun Nov 29 19:47   71/2021  Undelivered Mail Returned to Sender
&
```

After that all the commands in my first post function the same i.e. *sudo mail* from user is successful, but *sudo -i* & *sudo su* are unsuccessful.

---

### Post by dcstar on 2009-11-30
> **cross157 said:**
> Thank you for the reply, I tried *mail* command alone and here was the result:

```
cross157@ubuntu:~$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/spool/mail/cross157": 1 message 1 new
>N  1 MAILER-DAEMON@gma  Sun Nov 29 19:47   71/2021  Undelivered Mail Returned to Sender
&
```

After that all the commands in my first post function the same i.e. *sudo mail* from user is successful, but *sudo -i* & *sudo su* are unsuccessful.

That shows that the user mail command is working fine.

---

### Post by dcstar on 2009-11-30
> **cross157 said:**
> 
.......
After that all the commands in my first post function the same i.e. *sudo mail* from user is successful, but *sudo -i* & *sudo su* are unsuccessful.

**sudo -i** & **sudo su** are stand alone commands that spawn shells and cannot have anything following them.

---

### Post by cross157 on 2009-11-30
> And cron?

*mail* from the root crontab file still bounces back.

> sudo -i & sudo su are stand alone commands that spawn shells and cannot have anything following them. 

Yeah, I am just accessing the root login via these methods, if I access via *sudo su* or *sudo -i* after that the *mail* function does not work. But if I access root via *sudo -s* the *mail* command is successful

Here's the code:
```
cross157@ubuntu:~$ sudo su
root@ubuntu:/home/cross157# mail -s Test1 name@gmail.com < /home/cross157/Desktop/helloWorld.sh
root@ubuntu:/home/cross157# exit
exit
cross157@ubuntu:~$ sudo -s
root@ubuntu:~# mail -s Test2 name@gmail.com < /home/cross157/Desktop/helloWorld.sh
root@ubuntu:~# exit
exit
You have new mail in /var/spool/mail/cross157
cross157@ubuntu:~$ sudo -i
root@ubuntu:~# mail -s Test3 name@gmail.com < /home/cross157/Desktop/helloWorld.sh

```

---

### Post by kjohri on 2009-11-30
define environment variable EMAIL using following commands,

```
EMAIL=sender@domain
export EMAIL
```

then, use *mutt *

```
mutt -n -s "Subject of email" receiver@domain  <message.txt
```

---

### Post by cross157 on 2009-11-30
```
cross157@ubuntu:~$ EMAIL=name@gmail.com
cross157@ubuntu:~$ export EMAIL
cross157@ubuntu:~$ mutt -n -s "Test1" name@gmail.com </dev/null
msmtp: account default not found: no configuration file available
Error sending message, child exited 78 ().
Could not send the message.
cross157@ubuntu:~$ sudo mutt -n -s "Test2" name@gmail.com </dev/null **#Successful email**
cross157@ubuntu:~$ sudo su
root@ubuntu:/home/cross157# EMAIL=name@gmail.com
root@ubuntu:/home/cross157# export EMAIL
root@ubuntu:/home/cross157# mutt -n -s "Test3" name@gmail.com </dev/null
root@ubuntu:/home/cross157# exit
exit
You have new mail in /var/spool/mail/cross157
cross157@ubuntu:~$ sudo -s
root@ubuntu:~# mutt -n -s "Test4" name@gmail.com </dev/null **# Successful email **
root@ubuntu:~# exit
exit
cross157@ubuntu:~$ sudo -i
root@ubuntu:~# mutt -n -s "Test5" name@gmail.com </dev/null

```
Test 2 and Test 4 were successful as noted the rest failed, basically different command same problem. The root crontab did not work either :-(

---

### Post by kjohri on 2009-11-30
There may be some problem in the MTA configuration. To isolate the problem, use exim4 as the MTA and re-run the tests.

---

### Post by cross157 on 2009-11-30
> **kjohri said:**
> There may be some problem in the MTA configuration. To isolate the problem, use exim4 as the MTA and re-run the tests.

exim4 did the trick, must have been an issue with postfix configuration. Thank you for the suggestion. My root crontab is now able to send me emails. :-)

---

### Post by lazychris2000 on 2012-02-24
Sorry to revive such an old thread, but I am having the exact same problem.  I have been using ubuntu as my main OS for a few years and consider myself rather proficient in alot of things, but I am very new to configuring ubuntu to send email.  
```
To isolate the problem, use exim4 as the MTA and re-run the tests.
```
Any chance you could give me some help on how to do this?  I tried googling it, but my google-fu must be off tonight.

If it helps, I used [this]("http://code.google.com/p/klenwell/source/browse/trunk/projects/bash/mailx/setup_gmail_command_line.sh") script to configure the system for email: [http://code.google.com/p/klenwell/source/browse/trunk/projects/bash/mailx/setup_gmail_command_line.sh](http://code.google.com/p/klenwell/source/browse/trunk/projects/bash/mailx/setup_gmail_command_line.sh)

---

