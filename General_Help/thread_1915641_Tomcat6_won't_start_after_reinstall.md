---
title: "Tomcat6 won't start after reinstall"
date: 2012-01-26
forum: General Help
---

### Post by CryptiniteDemon on 2012-01-26
I tried to remove tomcat6 with apt-get purge, but it didn't delete /usr/share/tomcat6 or /var/lib/tomcat6 completely.  I manually deleted them both.
 

But then I tried to reinstall tomcat6 with apt-get install tomcat6 and then I couldn't get it to start no matter what.  I've tried to purge tomcat6-admin, tomcat6, and tomcat6-common after that to clean things out. 

I can't get the thing to start up no matter what.  Starting the process constantly fails.  Any ideas?

---

### Post by dragonfly41 on 2012-01-26
I have just gone through the process of **manually** installing tomcat7 into ubuntu-10.10 (rather than the tomcat6 in repository) and various tutorials helped ..

here is one ..

[http://diegobenna.blogspot.com/2011/01/install-tomcat-7-in-ubuntu-1010.html](http://diegobenna.blogspot.com/2011/01/install-tomcat-7-in-ubuntu-1010.html)

My tomcat7 is placed in /usr/local/tomcat7

[EDIT]

If you are purging an old installation, use command

locate tomcat

to find where it is installed

---

### Post by CryptiniteDemon on 2012-01-31
After about 6 hours of searching and trying different things, I ended up opening up synaptic and searching for tomcat and removing and servlet packages.  I also did a purge on eclipse.  

Then I reinstalled tomcat6 and the service started up fine.

---

