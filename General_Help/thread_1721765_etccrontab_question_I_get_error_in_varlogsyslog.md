---
title: "/etc/crontab question I get error in /var/log/syslog"
date: 2011-04-04
forum: General Help
---

### Post by highspider on 2011-04-04
[COLOR=SeaGreen]GREEN was changed for security reason[/COLOR]
[COLOR=Red]RED is error[/COLOR]

Apr  4 20:40:01 Server CRON[5666]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)

tail -f /var/log/syslog
```

Apr  4 20:40:01 Server CRON[5663]: (www-data) CMD ([ -x /usr/share/awstats/tools/update.sh ] && /usr/share/awstats/tools/update.sh)
Apr  4 20:40:01 Server CRON[5664]: (root) CMD (/usr/lib/cgi-bin/awstats.pl -config=[COLOR=SeaGreen]mysite.com[/COLOR] -update >/dev/null)
Apr  4 20:40:01 Server CRON[5665]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Apr  4 20:40:01 Server CRON[[COLOR=Red]5666[/COLOR]]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)
Apr  4 20:40:04 Server CRON[5659]: [COLOR=Red](CRON) error (grandchild #5666 failed with exit status 1)[/COLOR]
Apr  4 20:40:04 Server postfix/pickup[5376]: 40D1940999: uid=105 from=<munin>
Apr  4 20:40:04 Server postfix/cleanup[5684]: 40D1940999: message-id=<20110405034004.40D1940999@Server.[COLOR=SeaGreen]mysite[/COLOR].com>
....

```[COLOR=Blue]
[/COLOR][COLOR=Blue]I don't have a clue where this is coming from.[/COLOR]

---

### Post by highspider on 2011-04-05
Yeah solved 

[http://serverfault.com/questions/134748/munin-cron-fails-nothing-to-do-possibly-a-munin-conf-problem](http://serverfault.com/questions/134748/munin-cron-fails-nothing-to-do-possibly-a-munin-conf-problem)[FONT=Verdana]

[http://www.bluequartz.us/phpBB2/viewtopic.php?p=421724&sid=7f6d1c40521fb2536878379285f5ecbb](http://www.bluequartz.us/phpBB2/viewtopic.php?p=421724&sid=7f6d1c40521fb2536878379285f5ecbb)

[/FONT]```
sudo -u munin /usr/share/munin/munin-update --nofork --debug

```gave 
 [WARNING] about Server.[COLOR=SeaGreen]MYSITE[/COLOR].com

```

nano /etc/hosts

[COLOR=Red]192.168.0.104   Server.[COLOR=SeaGreen]MYSITE[/COLOR].com       Server[/COLOR]  
changed to 
[COLOR=Red]192.168.0.104  [COLOR=SeaGreen]MYSITE[/COLOR].com           Server[/COLOR]
``````
sudo -u munin /usr/share/munin/munin-update --nofork --debug

```Large list of output no [WARNING]'s

Basically the hosts names for server had an name Server. stuck in front of it when set up the server install

---

