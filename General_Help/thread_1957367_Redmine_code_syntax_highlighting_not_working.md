---
title: "Redmine code syntax highlighting not working"
date: 2012-04-12
forum: General Help
---

### Post by Budric on 2012-04-12
Hi,

I can't get redmine code highlighting to work under Ubuntu Server 11.10.  I've posted on their forum but got no help ([link]("http://www.redmine.org/boards/2/topics/29937")).  Sorry for cross posting, but I really need help resolving this issue and Ubuntu forums get more traffic/experience.

I followed this installation procedure [link]("http://www.redmine.org/projects/redmine/wiki/HowTo_Install_Redmine_in_Ubuntu").

Basically code highlighting doesn't work at all.  Not in the repositories, or in the wikis when you format using pre/code tags.  Redmine comes with coderay, after that didn't work I've installed Ultraviolet plugin but that doesn't highlight either.

I've tried:

[LIST]
[*]Installed rmagick.
[*]Admin/Information page shows all green ticks.
[*]There are no warnings/errors in /var/log/redmine/default/*
[*]/usr/share/redmine/vendor/plugins/ is owned and writable by www-data (that's the ubuntu's apache user I believe).
[*]made whole /usr/share/redmine owned/writable by www-data
[*]restarted apache2 service several times
[*]/etc/apache2/mods-enabled/passenger.conf does have PassengerDefaultUser www-data configuration
[/LIST]
[COLOR=#484848][FONT=Verdana]Some versions info:[/FONT][/COLOR]

[LIST]
[*]Redmine version: 1.3.2+dfsg1-1~oneiric+1
[*]ruby: 4.8~oneiric+1
[*]apache2: 2.2.20-1ubuntu1.2
[/LIST]
Has any successfully got it to work on their Ubuntu?  Any help with this?


Thanks.

---

### Post by Budric on 2012-04-20
bump

nobody at all has it working on their ubuntu 11.10?

---

### Post by Budric on 2012-04-24
Installed 1.4.1 from source (vs Ubuntu apt source) and code highlighting works.

---

