---
title: "Cannot send email in Evolution"
date: 2009-08-15
forum: General Help
---

### Post by sschr on 2009-08-15
Hello all:

I need help in configuring Evolution to send email. I can receive email from two POP3 accounts, but I cannot send.

Server: smtp.comcast.net

Thanks,
Scott

---

### Post by lejonmanen on 2009-08-19
Hello Scott,

you need to provide more information to get any help. What kind of error messages do you get? What client do you use?

---

### Post by vinnywright on 2009-08-19
> **sschr said:**
> Hello all:

I need help in configuring Evolution to send email. I can receive email from two POP3 accounts, but I cannot send.

Server: smtp.comcast.net

Thanks,
Scott

Evolution works fine hear with gmail........... but you nead to have all the setings just right check what comcast requiers for things like encription type and the sutch.

and for gmail eney way thars 2 servers

smtp.gmail.com ...........to send

imap.gmail.com .............to recev

so check it ALL agin :)

VINNY

O this was on Evolution 2.26.1 .....in Kubuntu 9.04 jj KDE 4.2.2

---

### Post by JDorfler on 2010-01-01
> **sschr said:**
> Hello all:

I need help in configuring Evolution to send email. I can receive email from two POP3 accounts, but I cannot send.

Server: smtp.comcast.net

Thanks,
Scott
Comcast SMTP needs you to send in port 587.  The problem is I don't know how to adjust ports in Evolution, which I'm trying to figure out now.  If this keeps up I'll just have to stick with Thunderbird.

---

### Post by salmonjj on 2010-01-05
This is a fairly old thread, but I'm having the same problem. Has anyone come up with an answer? It's difficilt to imagine that a piece of software as complete as Evolution wouldn't have a way to handle this problrm!

---

### Post by bkratz on 2010-01-05
> **salmonjj said:**
> This is a fairly old thread, but I'm having the same problem. Has anyone come up with an answer? It's difficilt to imagine that a piece of software as complete as Evolution wouldn't have a way to handle this problrm!

With my AT&T account it is done like this


[http://ubuntuforums.org/showpost.php?p=4398714&postcount=2](http://ubuntuforums.org/showpost.php?p=4398714&postcount=2)

I suspect that yours is similar.  (:XXX)

---

### Post by oldos2er on 2010-01-05
Set SMTP server configuration to comcast.com:587 (assuming comcast.com is the correct server name).

---

### Post by salmonjj on 2010-01-05
I found the answer on the Evolution board.
 
You need to use "smtp.comcast.net:587" as the server name.
 
Server type:             SMTP
Server configuration: smtp.comcast.net:587
Check thebox            Server Requires Authentication
Security:                   No encryption
Authentication type:   Login
User name:               You
 
When you do a send, you'll be asked for a password. Enter it and everything should work.

---

### Post by JDorfler on 2010-01-07
Yep, that did it.  That was good and now I'm using Evolution as my main email client.  (I'm not liking Thunderbird 3 in my Win 7 partition, and I know the next step in Ubuntu is Thunderbird 3.  Might as well use Evolution.  Also it helps that it corresponds great with Ubuntu One.)

---

