---
title: "Apache thread keeps freezing."
date: 2009-10-16
forum: General Help
---

### Post by StrangeWill on 2009-10-16
This is an issue I'm having with SugarCRM, but details lead me to believe it's an apache issue, I've put in a request for their help, but in case they turn me away citing Apache as the issue, I'd figure I'd ask here...


What I reported with them:
> 

Sugar Version: 5.2, 5.5RC (tried both, same issue)
Sugar Edition Sugar Community
Category: Modules
Operating System: Ubuntu 9.04
PHP Version: 5.2.6
Database: MySQL 5.0.75
Web Server: Apache 2.2.11

Steps to reproduce
1. Click "Load Modules" from admin menu
2. Everything will load fine.
3. Click anywhere else, Apache process is aready dead from the end of the last page call.

Only the load modules page does this, only this application, we host many applications and haven't had this issue before.


Error message or issue presented
Apache Log:
[Fri Oct 16 08:09:22 2009] [error] [client 172.16.100.184] File does not exist: /var/www/internal/crm/include/javascript/yui/ext/resources, referer: [http://172.16.100.20/crm/index.php?m...rd&view=module](http://172.16.100.20/crm/index.php?m...rd&view=module)
[Fri Oct 16 08:09:22 2009] [error] [client 172.16.100.184] File does not exist: /var/www/internal/crm/include/javascript/yui/ext/resources, referer: [http://172.16.100.20/crm/index.php?m...rd&view=module](http://172.16.100.20/crm/index.php?m...rd&view=module)
[Fri Oct 16 08:09:22 2009] [error] [client 172.16.100.184] File does not exist: /var/www/internal/crm/include/javascript/yui/ext/resources, referer: [http://172.16.100.20/crm/index.php?m...rd&view=module](http://172.16.100.20/crm/index.php?m...rd&view=module)
[Fri Oct 16 08:09:22 2009] [error] [client 172.16.100.184] File does not exist: /var/www/internal/crm/include/javascript/yui/assets, referer: [http://172.16.100.20/crm/index.php?m...rd&view=module](http://172.16.100.20/crm/index.php?m...rd&view=module)
[Fri Oct 16 08:09:22 2009] [error] [client 172.16.100.184] File does not exist: /var/www/internal/crm/include/javascript/yui/assets, referer: [http://172.16.100.20/crm/index.php?m...rd&view=module](http://172.16.100.20/crm/index.php?m...rd&view=module)
[Fri Oct 16 08:09:36 2009] [notice] caught SIGTERM, shutting down

^Me restarting Apache, it isn't responding.

SugarCRM Log:
Reports nothing.

I know it looks like an Apache issue, but why only this application, this page, and errors are reported with these scripts?

I've tried fresh installs of SugarCRM, both the stable and RC, no difference.

Thanks.



```

Apache Server Status for 172.16.100.20

Server Version: Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch proxy_html/3.0.1
Server Built: Aug 18 2009 14:27:36

Current Time: Friday, 16-Oct-2009 09:45:44 PDT
Restart Time: Friday, 16-Oct-2009 09:28:44 PDT
Parent Server Generation: 0
Server uptime: 16 minutes 59 seconds
Total accesses: 1919 - Total Traffic: 2.5 MB
CPU Usage: u3.12 s.67 cu0 cs0 - .372% CPU load
1.88 requests/sec - 2620 B/second - 1391 B/request
3 requests currently being processed, 8 idle workers

W___W___W__.....................................................
................................................................
................................................................
................................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

Srv	PID	Acc	M	CPU 	SS	Req	Conn	Child	Slot	Client	VHost	Request
0-0	19126	61/266/266	W 	0.81	276	0	100.7	0.36	0.36 	172.16.100.184	Server.local	GET /crm/index.php?module=Administration&action=index HTTP/1.1
1-0	19127	0/342/342	_ 	0.22	507	2	0.0	0.45	0.45 	172.16.100.183	Server.local	GET / HTTP/1.1
2-0	19128	0/445/445	_ 	0.27	246	0	0.0	0.59	0.59 	172.16.100.184	Server.local	GET /server-status HTTP/1.1
3-0	19129	0/104/104	_ 	1.10	402	557605	0.0	0.14	0.14 	172.16.100.184	Server.local	GET /crm/index.php?module=Administration&action=index HTTP/1.1
4-0	19130	1/157/157	W 	0.52	402	0	9.6	0.20	0.20 	172.16.100.184	Server.local	POST /crm/index.php HTTP/1.1
5-0	19131	0/38/38	_ 	0.41	403	569407	0.0	0.04	0.04 	172.16.100.184	Server.local	POST /crm/index.php HTTP/1.1
6-0	19174	0/209/209	_ 	0.13	124	0	0.0	0.28	0.28 	172.16.100.184	Server.local	GET /server-status HTTP/1.1
7-0	19175	0/163/163	_ 	0.15	517	0	0.0	0.22	0.22 	172.16.100.184	Server.local	GET /server-status HTTP/1.1
8-0	19176	3/93/93	W 	0.09	0	0	4.4	0.12	0.12 	172.16.100.184	Server.local	GET /server-status HTTP/1.1
9-0	19448	0/1/1	_ 	0.00	544	3	0.0	0.00	0.00 	172.16.100.183	Server.local	GET / HTTP/1.1
10-0	19775	0/101/101	_ 	0.09	412	0	0.0	0.15	0.15 	172.16.100.184	Server.local	GET /server-status HTTP/1.1

```
You can see the two frozen apache threads here, both on SugarCRM's directory (/crm), they'll sit for well over their allowed processing time (300s).

---

### Post by lavinog on 2009-10-16
please enclose the status page in code tags to preserve spacing:
[http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by StrangeWill on 2009-10-19
Any ideas?

---

### Post by lavinog on 2009-10-19
I would look at the access and error logs.

---

### Post by lavinog on 2009-10-19
[http://kb.sugarcrm.com/category/system/php/](http://kb.sugarcrm.com/category/system/php/)

---

### Post by Niko Johnson on 2009-10-19
have you tried restarting apache or killing all your apache process's and starting it back up 
```
 cd /home/www/apache/bin 
./apachectl restart
or
killall httpd
cd /home/www/apache/bin
./apachectl start

```

---

### Post by StrangeWill on 2009-11-01
> **Niko Johnson said:**
> have you tried restarting apache or killing all your apache process's and starting it back up 
```
 cd /home/www/apache/bin 
./apachectl restart
or
killall httpd
cd /home/www/apache/bin
./apachectl start

```
Oh restarting apache gets me back into the website, just every time I access this page apache dies.

> **lavinog said:**
> [http://kb.sugarcrm.com/category/system/php/](http://kb.sugarcrm.com/category/system/php/)

The issue isn't in there, SugarCRM guys are pretty much stumped, I'll do the error checking stuff, the thing is that the page that causes the Apache crash loads fine, it's just every request after that which cannot be completed.

Maybe the end of that page creates some kind of loop? I dunno I'll check the code for it I guess.

---

### Post by StrangeWill on 2009-11-01
> **lavinog said:**
> I would look at the access and error logs.

I'll check the access logs, error logs are blank.

---

### Post by StrangeWill on 2009-11-02
> **StrangeWill said:**
> I'll check the access logs, error logs are blank.

```

william@Server:/var/log/apache2$ grep UpgradeWizard *.log
access.log:172.16.100.184 - - [02/Nov/2009:13:06:48 -0800] "GET /dev/index.php?module=Administration&action=UpgradeWizard&view=module HTTP/1.1" 200 14895 "http://crm/dev/index.php?module=Administration&action=index" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/themes/TrailBlazers/images/show.gif HTTP/1.1" 200 97 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/container.js?s={$sugar_version}&c={$js_custom_version} HTTP/1.1" 200 68643 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/sugar_grp_yui_ext.js HTTP/1.1" 200 299282 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/tabview.js HTTP/1.1" 200 19741 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/ytree/TreeView/css/check/tree.css HTTP/1.1" 200 2590 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/assets/container.css HTTP/1.1" 200 3282 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/ext/resources/css/grid.css?1027 HTTP/1.1" 200 13198 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/ext/resources/css/toolbar.css HTTP/1.1" 200 1382 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/ext/resources/css/tabs.css?1030 HTTP/1.1" 200 4395 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/assets/tabview/css/round_tabs.css HTTP/1.1" 200 2586 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"
access.log:172.16.100.184 - - [02/Nov/2009:13:06:49 -0800] "GET /dev/include/javascript/yui/assets/tabview/css/tabs.css HTTP/1.1" 200 1884 "http://crm/dev/index.php?module=Administration&action=UpgradeWizard&view=module" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.14) Gecko/2009090217 Ubuntu/9.04 (jaunty) Firefox/3.0.14"


```
Nothing out of the ordinary, correct?

The page loads fine, all the way down to </html> so it's not dying mid process, unless it's doing something after the template finishes processing.

---

### Post by StrangeWill on 2009-11-02
Found out what it was, SUGARCRM is making an https query:
Mon Nov  2 13:13:12 2009 [26428][1][DEBUG] USING HTTPS TO CONNECT TO HEARTBEAT

However it's being denied by the firewall... I'm allowing destination 443, not source 443...

Weirdest part was that PHP would stall on the query and never time out, I guess it's a bug?

How can I securely allow this? I don't want someone making requests on port 22 from source 443... 

Or should I just run rule sets of deny on ports I'm sure I don't want them on?

---

### Post by lavinog on 2009-11-02
There are two ways a firewall can block access: deny and drop.
Deny informs the requestor that access is blocked, while drop will just ignore the request.  (drop is sometimes preferred because it slows down port scanners and reduces the chance of DOS attack)
what is likely to be the case is that the firewall is dropping the requests, and the server doesn't have a timeout set, so it is waiting forever.
The bug in this case is that the server or the program does not have a timeout set.

The better solution would be to open the port for the localhost on port 443.
I would also bring this up on the sugarcrm forums...they might have a better understanding of this.

---

### Post by StrangeWill on 2009-11-02
Yeah I posted it there, opened the port...

I just wanted to defend myself from someone getting the idea of requesting say... SSH from a program that uses port 443, my firewall would let it through...

Basically I just allow access based on requests made, and drop the rest. Should I allow access based on requests made to the server, allow requests based on the ports that are being replied on, then drop packets based on ports requested, THEN default to drop?

---

### Post by lavinog on 2009-11-02
> **StrangeWill said:**
> Yeah I posted it there, opened the port...

I just wanted to defend myself from someone getting the idea of requesting say... SSH from a program that uses port 443, my firewall would let it through...

Basically I just allow access based on requests made, and drop the rest. Should I allow access based on requests made to the server, allow requests based on the ports that are being replied on, then drop packets based on ports requested, THEN default to drop?

I am not sure how to answer your question.

The SSH concern is confusing also.  You shouldn't have ssh configured to accept connections on port 443.  Are you saying that users can use port 443 to connect to other servers via ssh? or are you concerned that they can establish a ssh connection to your server via port 443.
I am not familiar with sugarcrm nor its security issues.

---

### Post by StrangeWill on 2009-11-03
> **lavinog said:**
> I am not sure how to answer your question.

The SSH concern is confusing also.  You shouldn't have ssh configured to accept connections on port 443.  Are you saying that users can use port 443 to connect to other servers via ssh? or are you concerned that they can establish a ssh connection to your server via port 443.
I am not familiar with sugarcrm nor its security issues.
Well under an insane theory, couldn't you set a program to have the source port BE port 443, and then the destination port be 22. My firewall will say "oh port 443 source? Go ahead" (letting SSL requests go through so apache doesn't choke).

Of course I have SSH denied, but do I need to go through and deny all my services now?

---

### Post by lavinog on 2009-11-03
> **StrangeWill said:**
> Well under an insane theory, couldn't you set a program to have the source port BE port 443, and then the destination port be 22. My firewall will say "oh port 443 source? Go ahead" (letting SSL requests go through so apache doesn't choke).

Of course I have SSH denied, but do I need to go through and deny all my services now?

If it was possible, couldn't it be done with any outgoing port and not just 443?

---

### Post by StrangeWill on 2009-11-04
> **lavinog said:**
> If it was possible, couldn't it be done with any outgoing port and not just 443?
Not really, I'm allowing all inbound connections FROM port 443 (responding to SSL requests) so that SSL connections initiated by the server are allowed in and wont crash Apache.


To be honest, I can just black list all low-end ports for deny, allow certain ones through, and everything will be fine, just my rule list will be a mile long.

---

