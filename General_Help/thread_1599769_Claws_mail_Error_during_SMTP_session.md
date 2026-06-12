---
title: "Claws mail: Error during SMTP session"
date: 2010-10-18
forum: General Help
---

### Post by pinkpinkpinkpanther on 2010-10-18
Trying to transfer to  claws mail from kmail, I have problem in sending emails:
It doesn't send email through one of my accounts (a university account) and says: An "error happened during SMTP session".
My other university account works!
Have I done any stupid mistake in configurations?

Thx,
Pink Panther.

---

### Post by Old_Man_Unix on 2010-10-18
Even "well-known" mail servers like Gmail can be somewhat particular in their client configuration settings.  

Without knowing the specific mail server set-up of your university system, it would be impossible to even guess what the client configuration settings should be.

Your best bet is to contact the sysadmin of your mail system and ask them what configuration is required for a mail client.

Some of the "usual suspects":


[LIST=1]
[*]Account name incorrect (sometimes the whole address with the domain-name is required)
[*]Password incorrect
[*]No authentication when it is required
[*]Wrong type of authentication when it is required
[*]Incorrect security settings (SSL/TLS/STARTTLS)
[*]No port number when port numbers are required
[*]Wrong port number when port numbers are required
[/LIST]

If your sysadmin don't know from port numbers - and some of them apparently dozed off during that part of the training -  here are some of the more common port numbers that you may encounter

> smtp             25/tcp    Simple Mail Transfer

http             80/tcp    World Wide Web HTTP

pop3            110/tcp    Post Office Protocol - Version 3
imap            143/tcp    Internet Message Access Protocol

ldap            389/tcp    Lightweight Directory Access Protocol

https           443/tcp    http protocol over TLS

smtps           465/tcp    #smtp protocol over TLS (was ssmtp)
submission      587/tcp    Submission for Simple Mail Transfer

ldaps           636/tcp    sldap #ldap protocol over TLS

imaps           993/tcp    # imap4 protocol over TLS
pop3s           995/tcp    # pop3 protocol over TLSFair warning:  checking port numbers on your own is not for the fainthearted.  Try to find someone who knows.

Good luck.

---

### Post by pinkpinkpinkpanther on 2010-10-18
I checked out settings of my ex-client and I got that I have to use TLS not SSL, but in the configuration windows I Only see SSL and STARTTLS options. How can I change into TLS? 
I use IMAP.
btw, in my previous clients I used to use IMAP and deleting emails from client didn;t delete them from server, but in this claws this heppens. Can I change this somehow?

Thx again!

---

### Post by Old_Man_Unix on 2010-10-19
> **pinkpinkpinkpanther said:**
> I checked out settings of my ex-client and I got that I have to use TLS not SSL, but in the configuration windows I Only see SSL and STARTTLS options. How can I change into TLS? 
I use IMAP.
btw, in my previous clients I used to use IMAP and deleting emails from client didn;t delete them from server, but in this claws this heppens. Can I change this somehow?

Thx again!


To answer your first question, use STARTTLS.  You may have to declare the port number - see the list above or contact the mail system administrator. 

 Your second  question presents some problematic issues regarding the use of mail protocols. 

It's my understanding that since IMAP messages are actually accessed from the server and not kept locally, if you delete a message from ***any*** connected local client, you are in fact deleting it from the server.  

There is a way to keep a ***local copy*** of IMAP messages by setting up a separate mailbox folder on your client and copying the messages over to it from the IMAP mailbox.   The messages that are copied into that separate mailbox folder are actually physically on your local computer, and what you so with them locally does not affect the copy on the server.  

 There are plug-ins for some clients as well  separate applications that essentially set this up for you automatically or semi-automatically.  I don't know if there is such a plug-in for CLAWS,  but you can always do it manually without too much effort.  In my sysadmin days, we prepared cheatsheets that walked people through the steps - perhaps your university system has some of those as well. 

I'm sorry but I do not use IMAP an longer so I cannot be more specific than this.

---

