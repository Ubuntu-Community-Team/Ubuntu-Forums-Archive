---
title: "Evolution send port problem"
date: 2009-10-15
forum: General Help
---

### Post by johnmax on 2009-10-15
My ISP is now blocking port 25 for sending email and I need to change Evolution to port 587 but have been unable to do this. Help

---

### Post by akakingess on 2009-10-15
What have you tried, and/or what message are you getting or is it just not letting you access or even attempt to change it. Also, if you could post some more details, like is this on the Edgy machine that your profile shows you run, or something newer?

---

### Post by johnmax on 2009-10-15
I am running 8.10 on my desktop and 8.04 on my netbook. All was well for both sending and receiving email using Evolution until about 3-4 days ago when Verizon decided that email clients need to send using port 587 instead of port 25 (default). I have my XP laptop working with both Eudora & Outlook Express as port info was easily available in the preferences or option window but not so for Evolution. I can no longer send email but can still receive it.

---

### Post by plucky on 2009-10-15
> **johnmax said:**
> I am running 8.10 on my desktop and 8.04 on my netbook. All was well for both sending and receiving email using Evolution until about 3-4 days ago when Verizon decided that email clients need to send using port 587 instead of port 25 (default). I have my XP laptop working with both Eudora & Outlook Express as port info was easily available in the preferences or option window but not so for Evolution. I can no longer send email but can still receive it.

In evolution you have to specify the port number after the server information for each account.

Open **Edit > Preferences > Mail Accounts > Select Account > Edit > Sending e-mail** and add ":587" to the end of the server information.

```
pop.verizon.net:110
smtp.verizon.net:587
```


Good Luck

---

### Post by johnmax on 2009-10-15
I had already done that but forgot to mention it in my post last night. My ISP is Verizon but my email is not with them but a another ISP that I have had it with for more than a decade.

---

