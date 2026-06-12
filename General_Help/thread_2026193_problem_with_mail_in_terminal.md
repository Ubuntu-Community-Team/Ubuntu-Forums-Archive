---
title: "problem with mail in terminal"
date: 2012-07-14
forum: General Help
---

### Post by mijonuha on 2012-07-14
Hi
I read about mail in linux and I installed mailutils to send mail in command lines.
at first when I pressed ctrl+D to end the mail body, mail text ended. but the problem was that it didn't send mails at all. now moreover than that problem, even ctrl+D also does not work and after ctrl+D, I must use ctrl+C to end the mail. I dont know exactly what mistake I did during this time that now my ctrl+D does not work.
hence 2 questions:
1- when I want to send email is mailutils enough or I have to install any other service or do I need something like ssmtp?
2- why ctrl+D does not work but at first it was working? on a virtualbox it works but i dont want to reinstall my ubuntu. is there any program locking my ctrl+D or stopping me after pressing ctrl+D? if there is a program that I should uninstall? how can I recognize it? 

thanks so much

my terminal:
```

**aran@arvb:~$** df -h | mail -s "disk space report" mymail@gmail.com
the body of email
ggghhhjkkk.
^D^D^D^D^D^D^D^D [^D does not work]
^C
**aran@arvb:~$**

```in mail log the common error is:
```
 stat=Deferred: Connection timed out with alt4.gmail-smtp-in.l.google.com.
```

---

### Post by mijonuha on 2012-07-14
finally solved.
mail functions with delay. when you send email, it stops for a while. it does not mean that it is waiting for you to press ctrl+D so just be patient for a while.
I don't know how the other problem solved but after I installed SSMTP and it also failed, and after a while both worked for an unknown reason!

---

