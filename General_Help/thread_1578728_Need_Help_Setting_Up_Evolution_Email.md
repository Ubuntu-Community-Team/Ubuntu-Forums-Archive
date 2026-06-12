---
title: "Need Help Setting Up Evolution Email"
date: 2010-09-20
forum: General Help
---

### Post by Rachel5000 on 2010-09-20
Hello Gang,

I need help please.
 I have ATT/SBCGlobal and I want to use Evolution. 
I've used the Ubuntu Help Guy on Youtube, AT&T's tutorial, and a lot of directions from everywhere I can. This is my last hope.

 I tried AT&T live tech support, but as soon as I tell them I was running Ubuntu 9.10, they wanted to charge me $70 an hour. They did suggest I use one of their tutorials for Outlook (Express too) but nothing is working. I have no clue what's wrong. Can't send or receive email.  After I set up , the option to send/receive on email browser just disappears.

Any Help Appreciated,
Rachel

---

### Post by zealibib slaughter on 2010-09-20
Ok sbcglobal uses yahoo so this should work

you need to go to sbcglobal.net and log in to your email.  Go to the help section and find set up outlook
write down the following
recieving
Pop address ie pop.mail.sbcglobal.net or something like it
type of encryption none, ssl...
port 

sending
smpt address ie smpt.mail.sbcglobal.net or something like it
type of encryption
port

in evolution go to edit preferences mail accounts and double click on the account or set up a new one

at the incoming preferences screen enter the server ie pop.mail.sbcglobal.net or whatever you require but also add the port so it will look like this pop.mail.sbcglobal.net:110
choose what type of encryption and set it up for password

do the same for outgoing make sure to specify the port at the end of the server line like you did in incoming.

Yahoo uses different ports for different mail protocols they handle so setting the ports should help.

---

### Post by Rachel5000 on 2010-09-21
Thanks - I will try this rat now.
Rachel
:guitar:  <<<<<My Son. Dimebag Danny

---

### Post by dmp2010 on 2010-10-10
I have at&t yahoo. I tried all different things but nothing is working. Please help.

---

### Post by kc8hr on 2013-02-10
After struggling with Evolution for SBCGlobal.net without success, I went back to good ole Thunderbird. That being said, SBC has changed their server addresses:

POP: pop.att.yahoo.com
SMPT: smtp.att.yahoo.com

The Evolution setup program defaults to IMAP when I try to set up the account, and that just won't work. Has anyone succeeded using Evolution on

---

### Post by howefield on 2013-02-10
Old thread closed.

Please feel free to start a fresh one, you're more likely to get a response than tagging on to a 3 year old thread.

---

