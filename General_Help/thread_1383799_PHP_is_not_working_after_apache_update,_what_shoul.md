---
title: "PHP is not working after apache update, what should I do?"
date: 2010-01-17
forum: General Help
---

### Post by bobleny on 2010-01-17
When I go to localhost, and try to open any PHP file, it asks me to download the file rather than run it like it should. JSP doesn't appear to be working either. I'm not to concerned about the JSP though. This happened about a month ago, and has been driving me crazy...

I'm not sure how to trouble shoot the issue. I feel so stupid. :'(

Can anyone please help me. I'm running KUbuntu 8.04 with KDE 3 on a 64bit machine.

Thanks for any help!

---

### Post by john newbuntu on 2010-01-17
Is the apache server up and running? Is your document root set properly?

---

### Post by bobleny on 2010-01-18
Well, localhost won't load if apache isn't running, but I figured a manual restart wouldn't be a bad idea. When I ran the command though, I get this error:
```

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```

Despite the error, it does stop, start, and restart. To fix the error, I added the following to the httpd.conf file, an other wise empty file, located in the etc/apache2 directory.
```

ServerName 127.0.0.1

```

I'm not sure if that was a good idea or not, but it did stop the error message.

As far as the document root goes, I am seeing the appropriate files and directories when I load localhost. However, I did check the default file located in the /etc/apache2/sites-available directory, and the document root is set to the correct valid directory.

I should also note that the change to the httpd.conf file did NOT fix the main issue.

I hope this helps you help me, because I still don't know what to do...

---

### Post by Ahriman on 2010-01-18
Not meaning to come off as condescending, but you **did** install php, right?

---

### Post by john newbuntu on 2010-01-19
Can you restore your original httpd.conf file?

Then open a terminal and type 
```
hostname
```

Backup the file /etc/hosts.  Then make a change to /etc/hosts file as follows:

```
127.0.0.1 localhost
127.0.0.1 <hostname>

```
where <hostname> is what you got when you typed the original hostname command.

---

### Post by bobleny on 2010-01-19
Yes, PHP5-common has been installed. I did check to make sure it is still installed. MYSQL is also installed, and just in case you where wondering, so isn't kubuntu... LOL

The original httpd.conf file was blank, so I returned it so.

The hosts file already contained the following:
```

127.0.0.1	localhost
127.0.1.1	George

```

I did however change the 127.0.1.1 to 127.0.0.1. Still no change in the problem. Do I need to restart the computer in order for the IP change to take effect. I did restart the server of course.

This may help, when I try to run a PHP file, it tells me that it is a phtml file, not a php file. I find that odd.

---

### Post by john newbuntu on 2010-01-19
My /etc/apache2/html.conf file looks like this:
```
AddType application/x-httpd-php .php .htm .html
```
Add this, restart apache and try again.

---

### Post by bobleny on 2010-01-21
I don't have an html.conf file, so I created it and added what you suggested and restarted apache to no avail. Just in case you meant for that to go in the httpd.conf file, I tried it there too. Yet again, no luck...

I decided to reinstall apache and php, I ended up with the same issue. I read on and found something about enabling php...
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
> 
You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it. 


I've never had to do that before. I don't understand what changed. In the past, I just installed apache and PHP, changed the default root directory and it worked. I also don't understand why I would have to enable PHP after the apache update, you would think it would already be enabled...

Anyways, it works now. Thank you for all of your help!

---

### Post by junapp on 2010-01-21
> **john newbuntu said:**
> My /etc/apache2/html.conf file looks like this:
```
AddType application/x-httpd-php .php .htm .html
```Add this, restart apache and try again.
this could/should really be in /etc/apache2/mods-available/php5.conf

---

### Post by john newbuntu on 2010-01-21
Sorry, in post 7 I meant httpd.conf.

---

