---
title: "How to install RequestTracker"
date: 2012-10-02
forum: General Help
---

### Post by IvanMP on 2012-10-02
Hi all,
Can someone point or tell me how to install the latest version of Request Tracker system on Ubuntu Server 12.04, on a simple way or some other way. 

Tnx in advanced !

---

### Post by oldos2er on 2012-10-02
Installation instructions are in the README: [http://bestpractical.com/rt/docs/latest/README.html](http://bestpractical.com/rt/docs/latest/README.html)

---

### Post by IvanMP on 2012-10-02
Im reading that thing right now and on ./configure i get this errors:

> 

checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for chosen layout... relative
checking if user www exists... not found
checking if user www-data exists... found
checking if group www exists... not found
checking if group www-data exists... found
checking if group rt3 exists... not found
checking if group rt exists... not found
checking if group www-data exists... found
checking if database name is set... yes
checking if database name is valid... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/tmp/rt-4.0.7':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details



and in config.log beside lots of text, the one that i think that can help you to help me is 

> 
## ----------- ##
## Core tests. ##
## ----------- ##

configure:2006: checking for a BSD-compatible install
configure:2074: result: /usr/bin/install -c
configure:2088: checking for perl
configure:2106: found /usr/bin/perl
configure:2119: result: /usr/bin/perl
configure:2497: checking for chosen layout
configure:2510: result: relative
configure:2665: checking if user www exists
configure:2671: result: not found
configure:2665: checking if user www-data exists
configure:2668: result: found
configure:2689: checking if group www exists
configure:2695: result: not found
configure:2689: checking if group www-data exists
configure:2692: result: found
configure:2712: checking if group rt3 exists
configure:2718: result: not found
configure:2712: checking if group rt exists
configure:2718: result: not found
configure:2712: checking if group www-data exists
configure:2715: result: found
configure:2744: checking if database name is set
configure:2747: result: yes
configure:2755: checking if database name is valid
configure:2758: result: yes
configure:2849: checking for gcc
configure:2879: result: no
configure:2942: checking for cc
configure:2989: result: no
configure:3045: checking for cl.exe
configure:3075: result: no
configure:3099: error: in `/tmp/rt-4.0.7':
configure:3101: error: no acceptable C compiler found in $PATH
See `config.log' for more details



any suggestions ?

---

### Post by Toz on 2012-10-02
You don't have a compiler installed. Look for the build-essential package and install it. (Based on the readme file, it looks like you may need some more dev dependencies installed).

However, why not just install it from the Software Centre? It looks like version 4.0.4 is in the Universe repository:
```
apt-cache show request-tracker4
```
...to view the info about the package, and
```
sudo apt-get install request-tracker4
```
...to install it.

---

### Post by IvanMP on 2012-10-03
i did like you tell me i apt-get install request-tracker4 and i it ask me some questions and ect.... and im now lost ... how can i configure...

---

### Post by Toz on 2012-10-03
I am not familiar with the actual use of the product. To configure it, you will need to read the documentation that comes with it. The link mentioned above ([http://bestpractical.com/rt/docs/latest/README.html]("http://bestpractical.com/rt/docs/latest/README.html")) has configuration information starting at I believe point #7.

---

### Post by IvanMP on 2012-10-03
OK here it is 

I have a clear Ubuntu server 12.04 ... clear its mean, it have nothing except some software that on one point of installation asking you to install and that is DNS,OpenSSH, postgreSQL and ct.

So can some one help me or guideline me on how to install this Request Tracker and what things to configure ... PLS i need this ...

TNX in advanced !

---

### Post by electromage on 2013-03-29
> **Toz said:**
> You don't have a compiler installed. Look for the build-essential package and install it. (Based on the readme file, it looks like you may need some more dev dependencies installed).

However, why not just install it from the Software Centre? It looks like version 4.0.4 is in the Universe repository:
```
apt-cache show request-tracker4
```
...to view the info about the package, and
```
sudo apt-get install request-tracker4
```
...to install it.

It should be that simple, but I'm currently stuck in the same boat. I installed the request-tracker4 package, and supposedly I should be able to access the web GUI but I can't. There's nothing in /opt to link, and from what I can see, the service is running. All of the instructions are for a manual install, which is for an older version of Ubuntu, and I don't want to break anything. They want $2,500 for installation support, which is insane...

---

### Post by Toz on 2013-03-29
I just installed request-tracker4 on my 12.04.2 LTS server install. Here are the instructions I used (modified from [https://help.ubuntu.com/community/Request%20Tracker]("https://help.ubuntu.com/community/Request%20Tracker") because I'm installing version 4, not 3.8).


[LIST=1]
[*]_Install request tracker_
```
sudo apt-get install request-tracker4
```
...when prompted, answer as follows (my server name is ubuServ - you will see your server name instead):
	> rt.ubuServ = OK (accept default - note answer for apache2 config section)
	Handle RT_SiteConfig.pm permissions? = Yes
	Configure RT with dbcommon = Yes
	Initial root password = <enter a password> (make note of this password for later)

[*]_Configure request tracker_
Request Tracker Config files are in /**etc/request-tracker4/RT_SiteConfig.d** which will generate **/etc/request-tracker4/RT_SiteConfig.pm**
	Create: **/etc/request-tracker4/RT_SiteConfig.d/90-local** with the following content:
```
Set($MaxAttachmentSize , 10000000);
Set($FriendlyFromLineFormat, '\"%s\" <%s>');
Set(@ReferrerWhitelist, qw(x.x.x.x:80  SERVNAME:80));

```
...In the Set@ReferrerWhitelist parameter above, replace x.x.x.x with your server ip address and SERVNAME with your server name <- this will prevent the "possible cross site forgery" message - reference: [http://comments.gmane.org/gmane.comp.bug-tracking.request-tracker.user/68797]("http://comments.gmane.org/gmane.comp.bug-tracking.request-tracker.user/68797"))
Run: ```
sudo update-rt-siteconfig
```

[*]I _did no_t setup outbound email.
.
[*]_Apache2 config_
	Edit:** /etc/apache2/apache2.conf **
	...and add to end of file:
		```
ServerName rt.ubuServ
``` .....(replace ubuServ with name from first answer above)
	...Save
	Edit:** /etc/apache2/sites-available/default **
	...and paste _above_ the last "</VirtualHost>" parameter:
		```
Include /etc/request-tracker4/apache2-modperl2.conf
RedirectMatch ^/$ /rt 
```
	...Save
	Run: ```
sudo a2enmod rewrite; sudo service apache2 restart
```

[*]_Firewall_ - ensure that http is allowed: ```
sudo ufw enable http
```

[*]_Connect to rt via web browser_: [http://x.x.x.x/rt](http://x.x.x.x/rt) (where x.x.x.x is the ip address of your server)
	> login userid = root
	password = initial root password from above

[/LIST]

This gets the system installed and accessible via web browser. I did not setup email as note above in point #3, plus there are a couple of other configuration options from [here]("https://help.ubuntu.com/community/Request%20Tracker") (Configure RT & Inbound email config) that I did not complete. However, these instructions should get you an installed working RT.

---

### Post by electromage on 2013-04-12
Thanks **Toz**, that was very helpful in getting it up and running. Is there a reason the package doesn't set itself up that way?

---

### Post by Toz on 2013-04-12
No worries. The post install configurations need to be manual so as to not interfere with existing configurations or they require manual input. I don't think you'd want the package install to make those determinations on your behalf.

---

