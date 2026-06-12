---
title: "Help With Evolution Mail"
date: 2009-07-14
forum: General Help
---

### Post by kyle2595 on 2009-07-14
Hi, for some reason, Evolution Mail won't send emails.  It will receive them, and when I go to my email server (comcast.net) and send an email from the comcast.net web site it will send.  It will say "Sending message (100%)" and just stay at 100%, but it never sends the email.  If you can help, that would be great, thanks!

---

### Post by jonobr on 2009-07-15
What port njumber are you using for SMTP?

The default is 25 , but most providors block traffic on port 25 to stop mail relaying or spamming

A quick google for me indicates the smtp port is set to port 587

If you have that set already, then I recommend a packet trace

```
sudo tcpdump -vvv -i any port 587
```

The go to evolution and send the email.

If you see nothing, the email is not hitting the ethernet.
If you see a packet its being blocked from your network out.

---

### Post by kyle2595 on 2009-07-15
You had said:
> **jonobr said:**
> 

A quick google for me indicates the smtp port is set to port 587.
What did you google to find this out? (I'm sorry for asking a question that probaly has a very obvious answer, I'm not very good with computers).

---

### Post by plucky on 2009-07-15
> What did you google to find this out? (I'm sorry for asking a question that probaly has a very obvious answer, I'm not very good with computers).

See this [link](http://customer.comcast.com/Pages/FAQListViewer.aspx?topic=Internet&folder=6f4541ab-5423-47fb-a700-10806518e4d7#faq_breakout1) for Comcast email settings.


Evolution is an email client just like Outlook Express and uses the same settings, but in a different way.

To set the port number in evolution use **Edit > Preferences > Edit > Sending Email** and put in the server settings ```
smtp.comcast.net:587
``` will use port 587 for sending emails.

Good Luck

---

### Post by Nevart on 2009-07-15
I made a tutorial here that may help...

[https://www.lcwsoft.com/whmcs/knowledgebase/62/How-do-I-set-up-Evolution-for-use-with-my-sites-e-mail-accounts.html](https://www.lcwsoft.com/whmcs/knowledgebase/62/How-do-I-set-up-Evolution-for-use-with-my-sites-e-mail-accounts.html)

---

### Post by jonobr on 2009-07-15
Hey kyle2595

I put in something like comcast smtp (or maybe email) settings.
and it brought me to the Comcast homepage.

Typically the default port is 25 , however, not always the case

Cheers

---

### Post by kyle2595 on 2009-07-16
Thank you all so much, it worked!

---

