---
title: "Trying to kill internet process..."
date: 2006-03-08
forum: General Help
---

### Post by Mr Wrath on 2006-03-08
I am using a Sarge server with an Ubuntu back-up.  I have 15 M$ machines (slowly switching them to Ubuntu) using samba connections to the Sarge & Ubuntu servers.  In order to get on the internet, all machines have to go out through the server.  The question is..in the command line what can I type to kill one machines connection to the internet (temporarily).  I am somewhat new to networking by command line, but the info above is correct.

I appreciate any help someone can offer.

---

### Post by Mr Wrath on 2006-03-08
Edit: I am just looking for a general answer...not specifically for Sarge.  Just wanted to clearify that bit of information.

---

### Post by Prospero2006 on 2006-03-08
It sounds to me like you have 15 computers behind one gateway computer. 
Does the gateway masquerade the connections or what? 

In any event, you can use iptables to -DROP all packets that are outbound from any internal ip address. That will effectively kill the internet connection. Then you can delete the rule when you want to restore it. 

Pros

---

### Post by Mr Wrath on 2006-03-08
...what would the command be on a terminal session.

user@Ubuntu:/

---

### Post by Mr Wrath on 2006-03-08
..so...I do need to reconfigure some of the rules for the iptables or should it be more simple than that.

---

### Post by twigboy on 2006-03-09
I would try ifdown on each computer.  I dont know if you can do it remotely but I found this pretty good article [http://www.linux.com/article.pl?sid=06/02/01/168203](http://www.linux.com/article.pl?sid=06/02/01/168203)
But I have only used this on a Fedora system not a Debian.  At the end of the article its says there is a different command for Ubuntu.

---

