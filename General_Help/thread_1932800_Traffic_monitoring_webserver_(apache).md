---
title: "Traffic monitoring webserver (apache)"
date: 2012-02-28
forum: General Help
---

### Post by lt-mini on 2012-02-28
Hi all,

I was wondering if it is possible to get some logging/monitoring of traffic (up and down) from a web server?

Our websurver is running on ubuntu 10.04 LTS. At this moment I'm looking to the log files of apache (access.log) and looking at the tools netstat and apachetop.


What I want is to have on daily basis a report of the up and down traffic to that web server. Perl scripting is an option if i got the information. 

For example: 
Date             IN               OUT
28/02/2012      25MB              50MB
27/02/2012      500kB             200kB


Any suggestions are also welcome.

Kind Regards.

---

### Post by raja.genupula on 2012-02-28
[http://stackoverflow.com/questions/4764615/tracking-all-incoming-network-traffic-on-a-unbuntu-server](http://stackoverflow.com/questions/4764615/tracking-all-incoming-network-traffic-on-a-unbuntu-server)

[http://serverfault.com/questions/223106/tool-to-track-bandwidth-by-domain-name](http://serverfault.com/questions/223106/tool-to-track-bandwidth-by-domain-name)

---

### Post by Habitual on 2012-02-28
This script will 'ask' the webserver for it's sofware version every minute and mail you if it is NOT an apache string.

```

###
#!/bin/bash
# Written by root@cirrhus9.com
# Monitors an Apaceh server and emails the Admin if the
# server reports anything other than "Apache"
# http://bashscripts.org/forum/viewtopic.php?f=16&t=1522
# Last Edited on Thu Dec 29, 2011 - 10:11:40 PM EST
###
MAIL_ME="user@address.com"
MAIL_SUBJECT="Web_Server_needs_attention"
SERVER_DATE=$(TZ=PST8PDT date "+%a %b %d %I:%M:%S %p %Z")
LOCAL_DATE=$(date +%c)

# store this in a variable
IIS=$(curl -Is http://address.com | \grep -E '^Server' | cut -c9-21)
echo "$SERVER_DATE" - Web Server Check = "$WEB" >> ~/server.log

if [ "$WEB" = "Apache" ] ; then
exit 0
else
 echo "My_Server_Server_Check - FAILED" on "$LOCAL_DATE" | mail "$MAIL_ME" -s "$MAIL_SUBJECT"
 exit 1
fi
#EOF


```I used this to scan and report an IIS server and have modified it for Apache.
I run this as a regular user cron on my local computer and you can set the scan frequency there.

HTH.

---

### Post by btindie on 2012-02-28
Take a look at [AWStats]("https://help.ubuntu.com/community/AWStats"), it probably does more than you want but it'll take the hard work out of it :D

---

### Post by zeljkojagust on 2012-02-28
I think vnstat is exactly what you need! It's a great little console tool you can use to generate daily, monthly, yearly reports for your ethernet interface. Reports look something like this:

daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
     yesterday    465.76 MiB |  110.35 MiB |  576.11 MiB |   54.62 kbit/s
         today    283.29 MiB |   71.96 MiB |  355.25 MiB |   56.55 kbit/s

---

### Post by lt-mini on 2012-02-29
Hi all, 

Thanks already for all your hint and tips.
I will check them out one by one.

Kind Regards.

---

### Post by SlugSlug on 2012-02-29
webaliser is pretty good,

mines here of you want to take a look

[http://drunkenslug.com/webalizer/](http://drunkenslug.com/webalizer/)

---

### Post by lt-mini on 2012-02-29
Impressive SlugSlug !!

---

### Post by SlugSlug on 2012-02-29
It is quite cool, I like the 'Search Strings' and 'Referrers'

---

### Post by lt-mini on 2012-02-29
Thx all,

Testing webalizer and vnstat at this moment.

Looking great and what I wanted!

Thank guys!

---

