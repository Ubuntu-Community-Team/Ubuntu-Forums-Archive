---
title: "Evolution + Gmail syncing"
date: 2009-11-14
forum: General Help
---

### Post by Vibin Lakshman on 2009-11-14
If it asked , first of all apologise , can anyone point me a good tutorial to do this , thunderbird will also do . :)

---

### Post by undecim on 2009-11-14
[http://mail.google.com/support/bin/answer.py?answer=38343](http://mail.google.com/support/bin/answer.py?answer=38343)

That explains how to set it up in thunderbird. Setup for evolution should be similar

---

### Post by emigrant on 2009-11-16
[LIST=1]
[*]Log into your Google Mail account at [http://www.gmail.com]("http://www.gmail.com/")
[*]Click on the **settings** button in the top right hand corner.
[*]Choose the **Forwarding and POP** tab.
[*]Set to your personal preferences, one of the following **MUST** be selected.
[LIST]
[*]Enable POP for all mail
[*]Enable POP only for mail that arrives from now on
[/LIST]
 
[*]**Save** your settings.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=gmailsetup1.png[/IMG]
[/LIST]
 
[/LIST]
 
**Create Gmail Account in Evolution**

 This will set up Evolution to access your Google Mail account. If this is your first account to be set up, a wizard will open when you first start Evolution. Otherwise you will have to add an account by using the following Evolution menu item ***Edit>Preferences>Mail Accounts>Add*** 
 
**Receiving(POP) Mail**

 
[LIST]
[*]Server Type: **POP**
[*]Server: **pop.gmail.com:995**
[*]Username: **johndoe@gmail.com**
[*]Use Secure Connection: **SSL encryption**
[*]Authentication: **Password Authentication**
[/LIST]
 
**Sending(smtp) Mail**

 
[LIST]
[*]Server: **smtp.gmail.com**
[LIST]
[*]Note: Some ISPs block port 25, if you are having a problem sending mail, substitute **smtp.gmail.com:587** for the server information above.
[/LIST]
 
[*]Server requires authentication: **Checked**
[*]Security: **TLS encryption**
[*]Authentication: **Plain** or **Login**
[*]Username: **johndoe@gmail.com**
[/LIST]
 
**Evolution Account Assistant**

 This is a visual representation of the steps used to set up your account using the Evolution Account Assistant. 

[LIST=1]
[*]This is the first window of the Evolution Account Assistant, you will click forward.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup0.png[/IMG]
[/LIST]
 
[*]Here you will fill out your name and e-mail address, then click forward.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup1.png[/IMG]
[/LIST]
 
[*]Choose POP as the server type, fill in the server and username, select SSL encryption, password authentication, then click forward.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup2.png[/IMG]
[/LIST]
 
[*]Set this to your personal preference.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup3.png[/IMG]
[/LIST]
 
[*]Select SMTP as the server type, fill in server and username, check 'server requires authentication', choose TLS encryption, and Login authentication, click forward.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup4.png[/IMG]
[/LIST]
 
[*]This should already be filled in for you, click forward.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup5.png[/IMG]
[/LIST]
 
[*]You are now finished, click Apply.
[LIST]
[*][IMG]https://help.ubuntu.com/community/UsingGmailWithEvolution?action=AttachFile&do=get&target=evolutionsetup6a.png[/IMG]
[/LIST]
 
[/LIST]

[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)

---

### Post by emigrant on 2009-11-16
for pop and smpt servers, use these values; not the ones shown in the pic.

[B]pop.gmail.com:995

smtp.gmail.com:587[/B]

---

### Post by mithun.kamath on 2009-11-16
I feel in receiving options you should select "Leave Messages on server"

---

### Post by Vibin Lakshman on 2009-11-17
Thanks "emigrant " that was cool .. :p

---

