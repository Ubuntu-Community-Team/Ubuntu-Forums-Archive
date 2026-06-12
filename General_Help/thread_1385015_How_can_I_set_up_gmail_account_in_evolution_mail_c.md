---
title: "How can I set up gmail account in evolution mail client ?"
date: 2010-01-19
forum: General Help
---

### Post by brijith on 2010-01-19
Hi,

How can I set up gmail account in evolution mail client.I have tried it few times but failed to connect. another important info that I have to give is I am accessing internet through a proxy server. That might me the reason for the failure. Can any one help me to configure evolution so that it must work in a network having a proxied interment connection...

Thanks

---

### Post by scouix on 2010-02-26
Hi,
I have the same problem. When i'm connected behind a proxy, evolution can't connect to gmail. This happens since I've updated to Karmic. 
Any clue ?

---

### Post by brijith on 2010-02-26
> **scouix said:**
> Hi,
I have the same problem. When i'm connected behind a proxy, evolution can't connect to gmail. This happens since I've updated to Karmic. 
Any clue ?

Is it working before you updated to Karmic ?

---

### Post by scouix on 2010-03-01
Yes ! It worked perfectly when I was on Jaunty, Hardy and Feisty

---

### Post by brijith on 2010-03-01
> **scouix said:**
> Yes ! It worked perfectly when I was on Jaunty, Hardy and Feisty
What I got from googling this issue is, the proxy server might be  blocking the port that evolution uses. Some people suggested me to enable the ports to solve this issue. But I don't know how to do it in Squid proxy server...

---

### Post by scouix on 2010-03-01
Maybe I should explain my case more precisely.

I have 4 emails accounts : 1 for spam, 1 for friends/family/etc. [this the gmail account with IMAP], 1 for an association in which I work actively and 1 for work. Except the gmail account, all mailbox are configured to use POP/SMTP.

At home, everything works just fine. At work, I need to use a proxy server. My only email account working is my work account. I thought connexions to other POP/STMP servers were blocked, but I've asked to the network team of our lab and there is no filtering or restrictions for emails. Plus, before upgrading to Karmic, everything was working fine.

I've made a clean install, but, as my /home is on a separated partition, I never delete it and I configure Ubuntu to use this partition as /home everytime I upgrade. I never had a problem with this.

Hope this helps!

Tell me if you need more information

---

### Post by scouix on 2010-03-01
I have just seen your reply. I don't know neither ! I will try to find more information !

---

### Post by scouix on 2010-03-01
It seems that the problem is known (both on Launchpad and Gnome - bugzilla), it affects also epiphany and empathy. 

Hope this will be soon fixed !

---

### Post by scouix on 2010-03-01
The bug is that evolution doesn't use the proxy settings. It connects to internet like if there were no specific proxy configuration set on preferences.

---

### Post by brijith on 2010-03-02
> **scouix said:**
> The bug is that evolution doesn't use the proxy settings. It connects to internet like if there were no specific proxy configuration set on preferences.

If that is the case let us hope it will get fixed soon :)

---

