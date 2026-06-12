---
title: "Apache2 setup error"
date: 2011-03-04
forum: General Help
---

### Post by spindler on 2011-03-04
I recently had to reinstall Ubuntu because of some errors I have with php5.   I installed Ubuntu 10.10 with a LAMP.

In my old install I separated the HOME directory and put my website in the directory.  The file and folder permissions worked before I I did not change anything.   The only thing that changes would be the install upgrade to 10.10

I am now having some problems pointing the new install to my site located in the home directory.   I have a default web page that I can see using the command.  The default page is a simple one page php file.

The website is a word press website which accesses the MSQL database.   I imported the MySQL database into MySQL ok and updated the word press files to point to the database.

When I ran the word press install function  using  MYSITE/wp-admin/install.php  the program stated wordpress was already installed.

I copied and pasted the Virtual host file and reloaded and restarted apache2.  The file itself should be fine since I did not change anything.

I am accessing my site through firefox using the following:

[http://localhost/mysite](http://localhost/mysite)
 
When I attempt to load the page firefox takes a long time and never reaching the site....eventuality I get a file not found error. 

What could I be missing?  What did I fail to configure?

Spindler

---

### Post by spindler on 2011-03-04
I found I have had some other problems with the network.   The gobal IP address changed on me over night.  It took 1/2 hour for the new address to point correctly.   When I attempt to view my site  I get a new type of error.

The message starts 

FORBIDDEN

Yo do not have permission to acce3ss / on this server.

____________________________________________________
Apache/2.2.16/(Ubuntu) Server at [www.MYSITE](www.MYSITE)   port 80



This is tell me that somehow the server is rejecting all users including those from the Internet.  Which is not good. 

My home directory has permission set to 755 and is owned by root:root

The user folder and all sub folders pointing to the website have permission set to  755 user:user 

The files within the folder generally have permission 644


II am not sure why everyone is denied access to my website.  Any idea how I can fix this?

Spindler

---

### Post by vivek.pandey on 2011-03-04
> **spindler said:**
> I found I have had some other problems with the network.   The gobal IP address changed on me over night.  It took 1/2 hour for the new address to point correctly.   When I attempt to view my site  I get a new type of error.

The message starts 

FORBIDDEN

Yo do not have permission to acce3ss / on this server.

____________________________________________________
Apache/2.2.16/(Ubuntu) Server at [www.MYSITE](www.MYSITE)   port 80



This is tell me that somehow the server is rejecting all users including those from the Internet.  Which is not good. 

My home directory has permission set to 755 and is owned by root:root

The user folder and all sub folders pointing to the website have permission set to  755 user:user 

The files within the folder generally have permission 644


II am not sure why everyone is denied access to my website.  Any idea how I can fix this?

Spindler

for the forbidden error thing see this thread
[http://ubuntuforums.org/showthread.php?t=1698478](http://ubuntuforums.org/showthread.php?t=1698478)

---

### Post by SeijiSensei on 2011-03-04
Start by looking at /var/log/apache2/error.log.  See if you can figure out why the requests are denied.

Permissions problems with Apache can happen at *both* the application level and the OS level.  At the OS level, the user www-data must be able to list and read all the website's files.  Apache provides another layer of permissions controlled by directives like "[Allow]("http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow")."

---

### Post by spindler on 2011-03-04
I do not think   using chmod -R +X  is going to help.  This command only adds a new level of permission.  I tried randomly changing permission before and this type of approach generally causes more problems.


I like what Seijisensei is stating.   BY looking at the log file I get a error with the .htaccess.  Here is a sample of the error report.

[Fri Mar 04 14:01:51 2011] [crit] [client 142.30.138.143] (13)Permission denied: /home/user/www/mysite/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Fri Mar 04 14:01:52 2011] [crit] [client 142.30.138.143] (13)Permission denied: /home/user/www/mysite/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable


It states that there is a  permission denied issue with the .htaccess file.


MY .htaccess  file has a permission of  744 and is owned by  USER:USER

--rwxr----r--    user:user  .....   ,htaccess


I also have double checked my virtual host file to make sure I am allowing access.  I have not changed the file since I reloaded Ubuntu so it should be good.    Here is the file. 

<VirtualHost *:80>
    ServerAdmin [EMAIL="user@mysite.com"]user@mysite.com[/EMAIL]
    ServerName mysite.com
    ServerAlias *.mysite.com

    DocumentRoot /home/user/www/mysite
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/user/www/mysite>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


It looks like Apache2 might not be able to read the .htaccess file.   How can I let www-data  read the user files? 

Any other ideas as to how can I get the system to read the .htaccess file?

Spindler

---

### Post by vivek.pandey on 2011-03-04
do you think you have some other server running on same port or something?

---

### Post by spindler on 2011-03-04
I do not have any other server on my network.    Why do you ask?  What are you thinking about?

---

### Post by vivek.pandey on 2011-03-04
no this was what actually happened with me . i too was getting a forbidden mesage. it was due to that cherooke thing.that image crap. i removed it and problem was solved so you too check that
ls -l /var/www/

---

### Post by spindler on 2011-03-04
OK... I think I fixed the .htaccess problem  as I noticed that the very last directory in the string did not have the permission required.  So I changed that and the error has not changed.   Further I noticed that all of the directories in my website directory all have a permission of 700.

I am not sure how this happened.   I backed up the directory before I reinstalled Ubuntu and I guess the folder permission changed at some point.


I am look at a new problem now.  How do I chmod recursively directors only. 

I found this code online somewhere 


find . -type d -exec chmod 755 {} \;

Of course when I tried I was told it is not recognised. Has Ubuntu deleted the find command ?

How do I recursively change directories only in my website directory?

---

### Post by spindler on 2011-03-04
Thanks everyone for your help.

I tried the command again and it seamed to worked after I vented on the forum.

---

### Post by vivek.pandey on 2011-03-04
can you please tell what you did next so that it worked?
thanx

---

