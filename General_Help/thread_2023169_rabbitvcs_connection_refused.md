---
title: "rabbitvcs connection refused"
date: 2012-07-12
forum: General Help
---

### Post by sdpagent on 2012-07-12
Dear all,
I keep getting the following error:
[IMG]http://img1.uploadscreenshot.com/images/orig/7/19218142999-orig.png[/IMG]

I checked iptables and it allows my ip. I also tried changing the conf file so that it allows 
* = rw

It never asks me for my login details. The same error occurs if you initiate from cli or nautilus3. Has anyone else come across this?

---

### Post by spjackson on 2012-07-12
I've never used rabbitvcs, but in general 'connection refused' means that the server is not listening on the port that you are trying to use. This could be a temporary problem, if the host is up but the relevant service is down.

If the problem persists, then has your configuration changed?

Perhaps it could be a firewall blocking the relevant port, but I'd normally expect 'connection timed out' in that case.

If nothing has changed at your end, check with incero.com.

---

### Post by sdpagent on 2012-07-13
Turns out the server must have restarted or something. Running:
```
svnserve -d -r /svn/directory/here
```
worked. How do I make sure this runs on every start up etc? (CentOS server)

---

### Post by spjackson on 2012-07-13
> **sdpagent said:**
> Turns out the server must have restarted or something. Running:
```
svnserve -d -r /svn/directory/here
```worked. How do I make sure this runs on every start up etc? (CentOS server)
The simplest method is to add your command to rc.local. I understand that on CentOS, this is in /etc/rc.d/ whereas on debian based systems like Ubuntu, it is in /etc.

---

