---
title: "Sharing a folder with windows via commandline"
date: 2011-12-19
forum: General Help
---

### Post by cyclobs on 2011-12-19
Okay so i have a Ubuntu web-server running here that i'm using for an intranet server. I've just set up an 'testing' section on the server so i can play with the site before it goes on release.

How do you share folders with windows machines from Linux using the command line? (being an server i have no GUI)

---

### Post by thaelim on 2011-12-19
You'll want to modify the Samba configuration in /etc/samba/smb.conf. See ```
man smb.conf
``` for more help

---

### Post by mbuell on 2011-12-19
Yeah - you need to study up a bit on Samba. Not hard really - pretty simple - but it is a little bit of a learning curve. 

You will have to add users, add user passwords, set security, etc. Example - you can set your security wide-open and avoid setting individual users - but then your security is wide-open and all your users can see each other's files. Now, traditionally (as in Novell) this was regarded as extremely bad practice. I can see reasons - you wouldn't want Julia opening George's porn files that he downloads at lunch. And you wouldn't want Bobby taking a look at Henry's (he's our virtual CFO) financial files and reports - after all - Bobby could see what everybody else was making (salary-wise) - and might make real trouble. How about an engineering firm - got an engineer working on some cool stuff - but a disgruntled person over in the next office - that disgruntled person might be able to sell that cool stuff the engineer is doing. So - open access can be a bad idea. 

You have to turn it on after rebooting - but you can make that automatic. But you will have to learn how to do that. You can shut it down if you have a problem, and restart it when you are ready - without rebooting the whole machine - but you have to know the CLI commands to do that, eh?

So, samba tutorials are probably a good thing to check out.

---

### Post by seawolf167 on 2011-12-19
Sharing is pretty easy via samba - take a look at these guides:
Here is the [server guide]("https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html") for Samba, here is another documentation [guide]("https://help.ubuntu.com/community/Samba") for samba.

---

