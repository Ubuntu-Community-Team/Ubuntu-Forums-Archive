---
title: "can't send or receive e-mail using Thunderbird"
date: 2010-05-28
forum: General Help
---

### Post by sham08 on 2010-05-28
Hello.I'm having trouble to send and receive e-mail using Thunderbird 3.When I tried setting up new account using the automatic configuration method,the result of scanning pop. and smtp. server returned 'none' with this orange circle.I assume it's the same problem that occurred when I first tried to install Evolution.But oddly,I manage to access the web-mail account provided by the ISP using the same information used to set-up Evolution and Thunderbird 3.Precisely I'm from Malaysia and the ISP is Streamyx.com.PC run on Ubuntu 9.10.And I've heard that the ISP is non-friendly of non standard e-mail applications.Hope someone could help me on this,and thanks in advance for any responses.

---

### Post by cryptotheslow on 2010-05-28
Thunderbird is about as standard as a mail client gets and will work with POP3, SMTP & IMAP perfectly well.

When the auto-detection of servers fails, have you tried clicking the "Manual Setup..." button then going to the Server Settings of the new account and adding your servers manually there?

---

### Post by littleknowledge on 2010-05-28
You may need to set up the POP settings manually and then enter the smtp information that your ISP provides for you.   
 
To elaborate: are you setting up an email that was provided by your ISP or created by someone in a different domain?  It makes a difference because if your ISP provided the settings, manually enter them as is.  If you have your own pop mail account somewhere else, you will need to setup the pop information of the external server but the SMTP information of your ISP.

---

### Post by sham08 on 2010-05-29
Thanks to cryptotheslow and littleknowledge,as my thread had keep your attention.Sorry for this late response.I've only have gmail as my main e-mails methods,and beside it,the default web-mail account provided by the ISP (Streamyx.com).I'm sure that I've configured Thunderbird rightly but according to an article that I've ran into yesterday,the ISP (Streamyx.com) had blocked the 25 port (for anti-spam purposes).The article was published in 2006 and unfortunately I've never knew about it.So,any ideas to how should I overcome this problem?Thanks.

---

### Post by John Bean on 2010-05-29
You need to find out which port they are using instead of 25 and enter it manually into TB's SMTP settings. Many servers now only allow authenticated SMTP on high numbered ports these days; Thunderbird can be configured to use whatever your ISP provides.

---

