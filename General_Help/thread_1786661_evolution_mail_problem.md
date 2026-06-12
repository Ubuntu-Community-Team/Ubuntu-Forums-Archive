---
title: "evolution mail problem"
date: 2011-06-19
forum: General Help
---

### Post by ptminh20 on 2011-06-19
hi every body ...
i have one problem with e-mail now.
when i turn it on, it cannot fresh inbox mail and to give me an announcement that:
>>>> error while refreshing folder inbox
 therefore,i am not feasible to receive any one mail from other. i had seen new mail when i use browser to check mail. however when i use evolution is impossible.  
I am just a newbie in Ubuntu and English, so sorry if i got somethings wrong in my words. 
thank for your help.

---

### Post by dFlyer on 2011-06-19
Welcome to the forum

Are you using Ubuntu 11.04 or an older version?

---

### Post by ptminh20 on 2011-06-19
yup. i am using Ubuntu 11.04 now.

---

### Post by ptminh20 on 2011-06-21
no boy can help me ....T_T

---

### Post by dFlyer on 2011-06-21
Have you double checked your mail settings, for both sending and receiving? What mail service are you using?

---

### Post by ptminh20 on 2011-06-21
i think server is normal. because i can check new mail by using browser. 
last week, it still working good. nothing has been changed. one day, I open evolution mail, and see that announcement that have something wrong when refresh inbox folder. 
 it cannot update new mail in inbox. however, It is usual sending mail to other. 
i am using IMAP+.
i had set up: imap.mail.yahoo.com
secure connection: SSL
.....
i had done something like tutorial on ubuntu help site.

---

### Post by terrykiwi83 on 2011-06-21
Am sure Yahoo only allows IMAP for client devices such as blackberry's; PDA..etc

Desktop systems are apparently not supported, search Yahoo IMAP Settings on Google lots of articles about this.

---

### Post by ptminh20 on 2011-06-22
oh men, I have been using IMAP to send and receive mail everyday. Iam sure about that. I had found on google how to set yahoo mail with IMAP on evolution mail, and here is result: 
"http://askubuntu.com/questions/20075/connecting-yahoo-mail-with-evolution"
 It's really useful. 
 I had posted this tutorial on ubuntu 4rum of Vietnamese,some members used it and they told me it worked well.

---

### Post by tredegar on 2011-06-22
Try this:

Close evolution.

Open the directory **~/.evolution/mail/local**

Delete the files **Inbox.cmeta Inbox.ibex.index Inbox.ibex.index.data**
_Do not delete_ the file **Inbox** because this holds your mail, the other files just hold indexes to your mail.

Restart evolution. The **Inbox.cmeta Inbox.ibex.index **and** Inbox.ibex.index.data** files will be re-created. This may take some time if you have a lot of mail.

Does it work better now?

---

### Post by ptminh20 on 2011-06-22
I will try to do it now. 
I think u r right, because my inbox folder has a lot of mails, i think it's rather than 500
^^

---

### Post by ptminh20 on 2011-06-22
It was solved every body. thank so much.

---

