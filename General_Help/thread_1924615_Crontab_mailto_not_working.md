---
title: "Crontab mailto not working"
date: 2012-02-13
forum: General Help
---

### Post by sangramanand on 2012-02-13
we are using a ubuntu server 10.04 for cronjobs execution
i added 14 scripts as cronjobs in root crontab  with mailto as my mail id.

I was receiving the cronjob emails regularly, but from the past 2 days am not receiving any cron job mails, i checked the logs for the 14scripts and they all are executed as per schedule and the tasks that they meant to do are successful. But sending the cronjobs mails are failing.

I tried reinstalling the sendmail service but the the terminal shows sendmail service is already installed in your system.



--
Thanks

---

### Post by Khayyam on 2012-02-13
sangramanand ...

Is your sendmail configured to recieve incomming mail and does it have an MX (mail) record?

If you have bind-utils installed, you can check the MX with the following:

```
nslookup type=MX <hostname of server>
```

Given that it was working until two days ago, it sounds to me like you had a mail delivery problem, and as the recipeint mailserver can't return the mail, or inform you that mail is being held until it can be delivered, it gives up.

So, unless your mailserver has a world accessable IP and domain name asigned (or an MX record that point to a mailserver that does), and can recieve mail, these things may happen from time to time.

Some mailservers will auto blacklist mail coming from badly configured mailservers (or mailservers it can't send delivery status to), and so future mail from cron may be dropped. This may be why you haven't had anything in the past two days. I'd suggest you contact your ISP if it continues.

HTH ...

---

### Post by SeijiSensei on 2012-02-13
Install the **mailutils** package.  Now you can send a message from the command prompt the same way crond does.

```
echo 'This is a test.' | mail -v -s 'test message' your_mailto_address
```

Replace "your_mailto_address" with the address you assigned to the MAILTO variable in your scripts.  The "-v" switch will provide a transcript of the transaction.

---

### Post by sangramanand on 2012-02-13
> **Khayyam said:**
> sangramanand ...

Is your sendmail configured to recieve incomming mail and does it have an MX (mail) record?

If you have bind-utils installed, you can check the MX with the following:

```
nslookup type=MX <hostname of server>
```

Given that it was working until two days ago, it sounds to me like you had a mail delivery problem, and as the recipeint mailserver can't return the mail, or inform you that mail is being held until it can be delivered, it gives up.

So, unless your mailserver has a world accessable IP and domain name asigned (or an MX record that point to a mailserver that does), and can recieve mail, these things may happen from time to time.

Some mailservers will auto blacklist mail coming from badly configured mailservers (or mailservers it can't send delivery status to), and so future mail from cron may be dropped. This may be why you haven't had anything in the past two days. I'd suggest you contact your ISP if it continues.

HTH ...

I entered the below command 
**$ps ax | grep sendmail** -  to check whether the sendmail process is running, and i would the above response.


**sendmail: MTA: rejecting new messages: min free: 100**
Is it because of the insufficient space that its not sending emails?

---

### Post by SeijiSensei on 2012-02-13
Yes.

Whenever you have a mail problem the first place to look for answers is /var/log/mail.log.  You would have seen this message in the log when it first began happening.

---

### Post by sangramanand on 2012-02-14
> **SeijiSensei said:**
> Yes.

Whenever you have a mail problem the first place to look for answers is /var/log/mail.log.  You would have seen this message in the log when it first began happening.


the mail.log file was empty, i couldn't find any errors in that.

---

### Post by SeijiSensei on 2012-02-14
You probably ran out of space in /var, since sendmail couldn't queue the messages in /var/spool/mqueue, nor write to /var/log/mail.log.

---

