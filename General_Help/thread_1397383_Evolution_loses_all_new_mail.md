---
title: "Evolution loses all new mail"
date: 2010-02-03
forum: General Help
---

### Post by aneganov on 2010-02-03
Hi all. 

Evolution problem - new messages are not shown in Inbox anymore starting from yesterday! I contacted to system administrator and he checked that messages are really downloaded from server. What could be the problem?

Help please!

---

### Post by SoFl W on 2010-02-03
Another computer downloading your messages.

---

### Post by aneganov on 2010-02-03
> **SoFl W said:**
> Another computer downloading your messages.

I think its impossible. Its corporate mail, no other computer having  login/password to be able to get mail.

---

### Post by aneganov on 2010-02-05
Still having the problem - No mail for 3 days. I see how Evolution downloads mail, but message are not appeared in inbox! Help!

---

### Post by plucky on 2010-02-05
Please check that the mail isn't being sent to the junk folder and then deleted on exit from evolution.

In evolution go to **Edit > Preferences > Mail Preferences > Junk** and un-check "Check incoming mail for junk". and see if that makes a difference.

Good Luck

---

### Post by CrazySat on 2010-02-05
Hi,

I have same problem too.

I don't know if it is an odd circumstance since I wanted to empty all cache folders:

```
/home/username/.evolution/cache/http

/home/username/.evolution/cache/tmp

/home/username/.evolution/mail/pop/xxxxx@xxxxx.xx/cache
```

I tryed to install again evolution from Synaptic

Anyway, I tryed to uncheck the option as suggested above and I will tell how is going ...

Thank you.

---

### Post by marcdet on 2010-02-11
The resetting of the filter did the trick. Took me long enough to find this solution. Thanks.

---

