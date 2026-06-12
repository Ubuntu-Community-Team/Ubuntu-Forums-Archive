---
title: "problems with installing dansguardian on ubuntu"
date: 2009-10-06
forum: General Help
---

### Post by Duke555 on 2009-10-06
as per instruc. on [http://www.kathmannlabs.net/mediawiki/index.php/Dansguardian_Ubuntu_Linux_Install_how-to](http://www.kathmannlabs.net/mediawiki/index.php/Dansguardian_Ubuntu_Linux_Install_how-to)
everything worked except for the last command:
[I]root@ubuntu:/etc/dansguardian# sudo /etc/init.d/dansguardian restart
[/I]
Restarting DansGuardian:  * Restarting DansGuardian:                                                                                                         Error reading file: /etc/dansguardian/lists/blacklists/aggressive/domains
Error reading file: /etc/dansguardian/lists/blacklists/aggressive/domains
Error opening file: /etc/dansguardian/lists/blacklists/aggressive/domains
Error opening bannedsitelist
Error opening filter group config: /etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration files

it is driving me crazy. would anyone please help me?
someone suggested that i should 'check permissions" 
how do i do that?


thank you :)

---

### Post by brigaterosse on 2009-12-18
hey, it can be late for solution, i write again.  i had a similar problem. in your problem,  there is no folder such as aggressive in blacklists.  i solve it;  mkdir /etc/dansguardian/lists/blacklists/aggressive touch /etc/dansguardian/lists/blacklists/aggressive/domains  with right permissions (644)  or you can disable the conf files which says dansguardian should check the aggressive domains.  hope to work

---

