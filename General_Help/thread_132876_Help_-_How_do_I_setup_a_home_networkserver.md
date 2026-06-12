---
title: "Help - How do I setup a home network/server?"
date: 2006-02-19
forum: General Help
---

### Post by MJSOnline on 2006-02-19
Hi all.  I have a few questions with regards to a home network / server.

Ok I am looking at using Ubuntu as a network server for home use.

I will be using a laptop to link to it using ubuntu on the laptop if I can.  What spec do I need the laptop to be?  What spec do I need the server to be?  What about backups, firewalls and anti virus etc?

Also I have a 2nd laptop, Windows XP that needs to link to it too.

I want to use the server to share/download music, doc files, maybe host my website or internal website (links to docs, files sites) mail server too etc, but control it, (reboots, updates) etc,  from the 1st laptop, Ubuntu.  Both laptops are going thro a router and both need internet access and access to the networked printers, scanners etc.  Can I run sql on the server too?

How do I go about setting all this up?  I have a base unit, spec below in sig.
What is the diff between Apache or Samba?

What do I need?
Any help would be good, in idiot style would be great.  Thanks in advance.  Matthew

---

### Post by MJSOnline on 2006-02-19
Anyone? Matthew

---

### Post by wjp.reg on 2006-02-19
You could start by consulting the ubuntu wiki and [Ubuntu FAQ Guide]("http://help.ubuntu.com/starterguide/C/index.html"); SAMBA will allow you to access network shares between windows and linux.

I know that doesn't answer all your questions.

good luck with the rest.

P.S. [The Ubuntu 5.10 Starter Guide]("http://http://easylinux.info/wiki/Ubuntu") might also help.

---

### Post by knalle on 2006-02-19
[QUOTE=MJSOnline]
I want to use the server to share/download music,doc files,
[/QUOTE]
**samba** + [B]smbfs
[/B]
[QUOTE=MJSOnline]
maybe host my website or internal website (links to docs, files sites) mail server too etc,
[/QUOTE]
**apache** + **php**

[QUOTE=MJSOnline]
but control it, (reboots, updates) etc,  from the 1st laptop, Ubuntu. 
[/QUOTE]
try **webmin** a web driven admin system

[QUOTE=MJSOnline]
Can I run sql on the server too?
[/QUOTE]
yes **postgresql** or **mysql** are good choices

start searching and reading about these keywords

happy hacking!

---

### Post by MJSOnline on 2006-02-19
[QUOTE=knalle]**samba** + [B]smbfs
[/B]

**apache** + **php**


try **webmin** a web driven admin system


yes **postgresql** or **mysql** are good choices

start searching and reading about these keywords

happy hacking![/QUOTE]

Thanks knalle.  Whould all the apps run on one system?  Matthew

---

### Post by knalle on 2006-02-19
yes without problems, i have my ubuntu acting as fileserver with samba, webserver with apache+php and sqlserver with postgesql, all on the same machine while acting as desktop

---

### Post by MJSOnline on 2006-02-19
[QUOTE=knalle]yes without problems, i have my ubuntu acting as fileserver with samba, webserver with apache+php and sqlserver with postgesql, all on the same machine while acting as desktop[/QUOTE]

Ok.  Sound like a tall order to do.  My head already hurts.  Would a basic laptop running Ubuntu link into the server to share files easily?  What spec is your server?  M

---

### Post by knalle on 2006-02-19
you know my server is for development only i don't serve my live site from my own computer, but from a isp

but for development; my computer is a 2.6gh intel with 1gb ram and ich5 chipset, its easy. when you install the standard ubuntu breezy your half way there, just add sqlserver and apache and your basicly set to go for developing sites and fool around for testing.

but if you think about hosting on the web, live think twice with that hardware

---

### Post by MJSOnline on 2006-02-19
Ok.  So if I take out the hosting of an external website from the list, is the rest of it covered as above?  Thanks again. M

---

### Post by knalle on 2006-02-19
with a little thinkering everything you ask for is well proved for in ubuntu and linux in general, there are two things i would say to you since your a noob like me,

1: don't host a mailserver yourself, if you don't know what your doing you will become the target of spammers galore, use pop3 against your isp as usual and you got all the mail service you want before you know what your doing

2: laptops can be a bit hard when it comes to drivers, search around on linux forums for hardware support for your specific laptop, mostly this is sound and video problems that needs a bit of fixing. apache/php is a chapter on its own, start reading

happy hacking

---

### Post by MJSOnline on 2006-02-19
Ok.  Many thanks.  That great news on the mail server idea.  I wasnt to sure about it myself.  Thanks again. M

---

