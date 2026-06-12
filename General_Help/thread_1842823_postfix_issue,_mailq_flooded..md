---
title: "postfix issue, mailq flooded."
date: 2011-09-12
forum: General Help
---

### Post by Drenriza on 2011-09-12
Hi all.

On a server i got, i have postfix installed. And for some reason the server is trying to send a e-mail to ALOT of different users. I fear that somehow, for some reason its trying to spam different users. But i'm wondering.

I can see in my logs that the e-mail gets rejected by the recipient server, and their for they get pushed to the mailq quere. But how can i see what e-mail the system is trying to send out? I would like to see what it contains.

Thanks on advance.
Kind regards.

---

### Post by SeijiSensei on 2011-09-12
First thing is to test to see if your running an "open relay" by running [this test](http://www.spamhelp.org/shopenrelay/). 

If the answer is yes, you need to disconnect it from the Internet while you diagnose the problem.  Otherwise your server will start to appear on blacklists.

If you also support the "submission" port, 587, you need to test for that as well.  You may need to do this manually; Google for "test open relay port 587" for some pointers.

---

### Post by Drenriza on 2011-09-13
Hi Senji.

Is their a other methode to test if i got a open relay then using the script on the page? Since that is not possible.

Edit.
Cant i check the 587 port by
```
netstat -an |grep 587 |grep LISTEN
```

I dont see the port 587 on my grep.
But in my mail.log file i see
> Sep 11 09:57:08 serverName postfix/smtp[14879]: 250551B0CFE: to=<email@something.com>, relay=cluster9.xxx.xx.com[xxx.xx.xxx.x]
What does the Relay= mean? Does the Relay= mean that the server is relaying a e-mail from somewhere else?

Kind regards.

---

### Post by SeijiSensei on 2011-09-13
> **Drenriza said:**
> Is their a other methode to test if i got a open relay then using the script on the page? Since that is not possible.

Why?  If that one doesn't work, search Google for "open relay test".  You'll see other options.

> Cant i check the 587 port by
```
netstat -an |grep 587 |grep LISTEN
```

What happens if you run "telnet localhost 587"? If nothing replies, the port's not open.

> What does the Relay= mean? Does the Relay= mean that the server is relaying a e-mail from somewhere else?

No, it's the server that handles inbound mail for "something.com".

---

### Post by Drenriza on 2011-09-14
Is it possible in postfix 1.1.11-0.woody to block a recipient.
like [email]something@yahoo.com[/email]

And block the entire @yahoo.com domain?
From both sending and receiving. I cant seam to find much on this.

---

### Post by dcstar on 2011-09-15
> **Drenriza said:**
> Hi all.

On a server i got, i have postfix installed. And for some reason the server is trying to send a e-mail to ALOT of different users. I fear that somehow, for some reason its trying to spam different users. But i'm wondering.


Look in your log files to see what/who is submitting these mail messages, that is what the log files are for.

---

### Post by Drenriza on 2011-09-16
> **dcstar said:**
> look in your log files to see what/who is submitting these mail messages, that is what the log files are for.

#5

---

### Post by Drenriza on 2011-09-20
> **SeijiSensei said:**
> Why?  If that one doesn't work, search Google for "open relay test".  You'll see other options.



What happens if you run "telnet localhost 587"? If nothing replies, the port's not open.



No, it's the server that handles inbound mail for "something.com".

When i telnet localhost 587 it says "Unable to connect" "Connection refused"
Anyone know how its possible to 
in postfix 1.1.11-0.woody to block a recipient.
like [email]something@yahoo.com[/email]

And block the entire @yahoo.com domain?
From both sending and receiving. I cant seam to find much on this

---

