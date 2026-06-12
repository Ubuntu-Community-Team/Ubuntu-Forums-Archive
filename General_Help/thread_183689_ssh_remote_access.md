---
title: "ssh: remote access?"
date: 2006-05-28
forum: General Help
---

### Post by bullgr on 2006-05-28
hi...

I installed ubuntu file server in my workplace to share files from the server to the windows clients.
From my windows client i manage the server thru the ssh with "putty".

So, my question is, how can i access the server outside from lan (etc. home)?
Can i do this with the installed ssh server? Or i must done something else?

thank's

---

### Post by chrestomanci on 2006-05-28
Your problem will not be SSH, but the firewalls & routers at your. workplace. You need to approach the network admin at your office.

If that is you, then come back and we can help you, otherwise I think your sysadmin would be the best person to ask.

---

### Post by bullgr on 2006-05-28
I am the "network admin"...

But it's not so complicated, with hundrets of pc's behind cisco router's etc...
It's a small office, in a small town, with 5-6 pc's.

I am experienced with firewalls and routers. I just need to know, how i can access
the server from my home.

As i wrote, i have ssh server installed and manage the server from my
windows client with "putty" (localy).

Can i done this also outside from lan (if yes, then how) or whatelse must be done?

thank's :-D

---

### Post by nanotube on 2006-05-28
set up port forwarding, so that an external connection to port 22 goes to your internal machine's port 22.

---

### Post by chrestomanci on 2006-05-28
It can be done, but you need to take some propper advice, and ask yourself it it is realy necessary. What you want to do is to open a hole in your company firewall to let SSH traffic in. I have a similar hole in mine, and I get constant hack attempts trying to guess passwords. If anyone guesses right your system will be wide open.

---

### Post by bullgr on 2006-05-28
Please don't give me instructions about to setup firewalls or routers, i can handle with that. I need only to know what i have to use to connect to the remote pc? Can i do this with putty(thru ssh), ftp or from a web browser? What must i type?

Thank you for the quick response :-D

---

### Post by hw-tph on 2006-05-28
Just ssh to connect to it from your own (home?) computer: **ssh user@host**
But It does strike me as weird that you didn't know that when you are experienced with these things. Again: Is this really necessary? If it is, do consider using keys instead of passwords, and just changing the ssh port to something else than the standard will also greatly reduce the number of password guessing attempts.


Håkan

---

### Post by bullgr on 2006-05-28
Yes chrestomanci, you have right... maybe it's not necessary.

Even then i live in a small town, who the citizens can't understand the
differense between a pc and a toaster!!!

Even worse, i beg many times my boss to buy a router to be more secure
the lan, but he believes that the 25 euro switch are done his job well to!!!

So, why i need to care about the ssh hole? With this circumstanses i care
only to do my job easier...

---

