---
title: "nagios problems"
date: 2005-01-27
forum: General Help
---

### Post by radeon on 2005-01-27
Hello 

Sorry for my english ;)

So the problem is that Nagios wont work :(

what is nagios [http://www.nagios.org/](http://www.nagios.org/)
how to get it apt-get install nagios-mysql

first bug is that inatalation proces don't see the apache2, hmm where are the mails to developers of this package ? the problem is easy 

the main thing is that I make a nice configuration files in /etc/nagios
but when I want to check them by nagios -v nagios.cfg I get only some errors that I heve no service, hosts so one ... but I have the config files quite full, so i don't know what is going on :(

Bye

---

### Post by geep on 2007-01-24
for nagios to work please read the documentation on nagios.org

make sure you have apache installed and working before you start with nagios. If you install from the apt-get repository you still have to do a lot of tuning before nagios will work correcly.

I would advise you to install 

nagios-text - A host/service/network monitoring and management system

and no mysql. This will add a extra point of failure to your monitoring and is difficult to install 

apt-cache search nagios
nagios-common - A host/service/network monitoring and management system
nagios-plugins - Plugins for the nagios network monitoring and management system

---

