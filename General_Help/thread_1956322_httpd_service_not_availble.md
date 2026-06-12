---
title: "httpd service not availble"
date: 2012-04-10
forum: General Help
---

### Post by ESimard on 2012-04-10
Hi, running ubuntu 10.10 and trying to install zoneminder.

Docs say to start the service httpd.
After entering "service httpd start" I get the message 
"httpd: unrecognized service"

"sudo service httpd start" gives the same message.

Checking with Synaptic Package Manager I see that the following are installed:
   mini-httpd
   apache 2.2-bin
   apache 2.2-common
   libapache 2-mod-php5
   apache2
     plus a bunch of support files.

Since the service won't start, any advice on what else is needed?

Thanks in advance
_Ernie

---

### Post by wallaroo on 2012-04-10
Since Apache2 is installed there is a good chance the http processes are already running (but may not be called that anymore).

You can run the following command in a terminal to check..
```
ps -eaf
```If a series of 'httpd' entries or a series of 'apache' entries are reported then it's running.

You can also just enter 'localhost' in your web browser, and if you get a valid response, then Apache (and thus 'httpd') is running OK.

If so you can proceed with the rest of the 'zoneminder' installation/setup.

If the web server appears not to be running you can try starting it with..
```
sudo apache2ctl -k start
```
If you need to control the web server while installing, then you can use any of the following commands..
```
sudo apache2ctl -k stop
sudo apache2ctl -k start
sudo apache2ctl -k restart
```

---

### Post by Serpher on 2012-04-10
I believe in Ubuntu the service is called 'apache2'. Other said methods work but you could also:

```
sudo /etc/init.d/apache2 start
```

---

### Post by ESimard on 2012-04-11
Thanks, entering localhost proved it was working, my problem is further down the line.  Also the start and stop commands also work.
_Ernie

---

