---
title: "Apache2 server problems"
date: 2011-08-02
forum: General Help
---

### Post by LuniTux on 2011-08-02
Hello,

I am having a small problem with my apache server. I have setup the LAMP server via [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"). I have three websites that are on the same computer. The websites work correctly internally but when I test any of them outside the network, they all redirect to the same website.

[www.a.com](www.a.com)
[www.b.com](www.b.com)
[www.c.com](www.c.com)

All of these goto [www.a.com](www.a.com)
Also, if I enter the IP address of the website, I get the directory listing of /var/www instead of the apache page. Even stranger, I can access the websites correctly through the directory listing.

Let me know if I need to post any file contents.

Thanks,

---

### Post by Beacon11 on 2011-08-02
You may want to check out virtual hosts ([http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)).

---

### Post by LuniTux on 2011-08-03
I used a2ensite to add the websites to the sites-enabled folder. Then when I tried to restart apache,

```
sudo service apache2 restart
 * Restarting web server apache2          [fail] 
```

After viewing the log file: **/var/log/apache2/error.log**

I found this:

```
tail -n6 /var/log/apache2/error.log
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/www.mysite.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/www.mysite.com-error_log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /etc/apache2/logs/www.mysite.com-error_log.
```

So then I added the logs folder and restarted apache:

```
sudo mkdir /etc/apache2/logs
sudo service apache2 restart
```

Apache restart was successful!

I will test the server tomorrow to see if everything is working.

So for anyone else having problems with apache restarting:
[LIST][*]Make sure the website files are linked to the sites-enabled folder (a2ensite)
[*]Create the folder for the logs if it does not exist (mkdir)
[/LIST]

---

