---
title: "PHP5 w/Apache2 Issue"
date: 2011-02-18
forum: General Help
---

### Post by LiteDrive on 2011-02-18
I've been searching and searching all over, and before anyone asks - yes, I did restart apache2. Twice. The issue is that everytime I enter my /var/www/html folder, the files simply download and don't display. 

Is there anything I can post here to help with a diagnosis? This is becoming extremely aggravating. 

Thanks.

---

### Post by fragos on 2011-02-18
The default installs of apache and PHP aren't configured to execute PHP. What you need is /etc/apache2/httpd.conf with the following 3 lines. 

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

### Post by MockY on 2011-02-18
Is PHP properly installed?

```
sudo apt-get install php5 libapache2-mod-php5
```

---

### Post by LiteDrive on 2011-02-18
No dice. 

I tried both of your suggestions, and all I got were a ton of errors. : /

It may be helpful to note that all I have is apache2.conf in my /etc/apache2 folder. 

I even tried making a httpd.conf file, copied everything from the apache2.conf and pasted it into that. Upon the /etc/init.d/apache 2 restart, everything just became worse.

Any more suggestions?

---

### Post by fragos on 2011-02-18
httpd.conf and apache2.conf are separate files and can't be combined. There should be other files in there as well like ports.conf. All should have been created when apache2 was run the first time. The only configuration necessary is for PHP in the httpd.conf. Perhaps you installed one of the individual apache2 files instead of the apache2 meta package.

---

### Post by MockY on 2011-02-18
I suggest you reinstall it.
The easiest way is to do
```
sudo tasksel
```
and select LAMP Server. This will install MySQL as well, so if that is not what you want, then this method is not what you want. However, the install for Apache and PHP is flawless.

---

### Post by LiteDrive on 2011-02-18
I saw the ports.conf in there, but unfortunately no httpd.conf. Should I uninstall everything and just re do it all? If so, how should I go about this?

---

### Post by fragos on 2011-02-18
create httpd.conf with the 3 line from above. If it existed from the install it would be empty.

---

### Post by LiteDrive on 2011-02-18
I did that, and then I got this output:

```
 * Restarting web server apache2                                                [Fri Feb 18 20:13:51 2011] [warn] module php5_module is already loaded, skipping
[Fri Feb 18 20:13:51 2011] [warn] module php5_module is already loaded, skipping
 ... waiting [Fri Feb 18 20:13:52 2011] [warn] module php5_module is already loaded, skipping
[Fri Feb 18 20:13:52 2011] [warn] module php5_module is already loaded, skipping
                                                                         [ OK ]
```

And unfortunately still no dice. Any other suggestions? I do appreciate the help, by the way.

---

### Post by fragos on 2011-02-18
Open the browser and enter url [http://localhost](http://localhost). Apache installed with an index.html file in /var/www which will be run as a test. That is the folder that apache will execute PHP files from. It is owned by root.

---

### Post by LiteDrive on 2011-02-19
[FONT="Times New Roman"][SIZE="5"]It works![/SIZE]

This is the default web page for this server.

The web server software is running but no content has been added, yet.[/FONT]


Muchos grassias, senore.

---

### Post by lisati on 2011-02-19
> **MockY said:**
> Is PHP properly installed?

```
sudo apt-get install php5 libapache2-mod-php5
```

Sometimes you might need to clear your browser cache as well as/instead of this.

---

### Post by AMDave on 2011-02-19
Since you have already said that there was only one file in the /etc/apache2 folder before you tried the tasksel command that was suggested, I'd say there was already a problem with the previous install.

There is nothing in the tasksel man page to suggest that using the install option will do a re-install either, unfortunately.

Fristly, I'd suggest quite firmly that you use:

```
$sudo apt-get update; 
```

which will refresh you package library and then

```
$sudo apt-get install --reinstall apache2 php5-mysql libapache2-mod-php5 mysql-server; 
```

the "--reinstall" option tells apt-get to do just that, reinstall any packages that are in the list that may already have been installed.

next you should become familiar with the Ubuntu Community Documentation pages which are superbly helpful and educational. 
Such as:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Some other things you need to know are the changes in the defaults.
Yes, httpd.conf will be in the /etc/apache2/ folder
BUT it should be blank as this is no longer where the daemon gets its directives from. 
Best leave that file alone.
After the re-install, if you still have something in there, remove whatever you had added and save it as an empty file.

at this point restart your services and try the default page
[http://localhost](http://localhost) [as per fragos' post above
if you don't get the "It Works" page then check out your /etc/hosts file and make sure that the original details are still there
in mine the first line is "127.0.0.1       localhost"

Next thing I noted was that the PHP5 error output default is changed to 'Production' mode. It will not output error messages to the browser by default.

edit the file /etc/php5/apache2/php.ini
locate the display_errors directive and change the =Off to =On

now restart your apache2 service
upload your php pages
and you should be in business

for further and much more detailed information you can find a great deal of information on the Ubuntu Community Documentation pages

HTH

[EDIT - looks like you solved it while I was typing. Well done. - EDIT]

---

### Post by LiteDrive on 2011-02-19
Damnit, I tried that too and nothing.

I actually made a mistake on my last post: I thought it worked, and then I tried to upload a php file to avail. :(

The file still only downloads. I know my urls and directories aren't wrong - I've double checked them multiple times now. 

Something is wrong...

---

### Post by fragos on 2011-02-19
Make sure your opening it with a browser set to http:\\localhost. Only a web server can execute PHP.

---

### Post by LiteDrive on 2011-02-19
```
Error: The new file /usr/share/php5/php.ini-production does not exist!
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up mysql-server (5.1.49-1ubuntu8.1) ...
Setting up php5-mysql (5.3.3-1ubuntu9.3) ...
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I actually posted not knowing AMDave had posted before me, so I never really caught what he said until now. I just reinstalled everything as told, and found this error right afterward. 

As far as the documentation goes, I'll definitely check that, though if anyone knows anything regarding this, it would be very helpful.

I appreciate the patience from everyone here as well, so far you've all been very helpful and despite the problem not being completely solved yet, I've learned a lot regardless.

Edit: despite the error, it seems like my php is now displaying properly. So, I'm actually in business! Thank you so much! You were all a great help.

---

### Post by mahfud on 2012-11-15
this is my fault.. :(
How about with this ? :confused:
 when  i do...
```
$sudo apt-get update
```then

```
$sudo apt-get install --reinstall apache2 php5-mysql libapache2-mod-php5 mysql-server
```and the result
```
root@jm-M2009:/home/jm# apt-get install --reinstall apache2 php5-mysql libapache2-mod-php5 mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/79.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 304975 files and directories currently installed.)
Preparing to replace apache2 2.2.20-1ubuntu1.3 (using .../apache2_2.2.20-1ubuntu1.3_i386.deb) ...
Unpacking replacement apache2 ...
Preparing to replace mysql-server 5.1.66-0ubuntu0.11.10.2 (using .../mysql-server_5.1.66-0ubuntu0.11.10.2_all.deb) ...
Unpacking replacement mysql-server ...
Preparing to replace php5-mysql 5.3.6-13ubuntu3.9 (using .../php5-mysql_5.3.6-13ubuntu3.9_i386.deb) ...
Unpacking replacement php5-mysql ...
Setting up libapache2-mod-php5 (5.3.6-13ubuntu3.9) ...
Error: The new file /usr/share/php5/php.ini-production does not exist!
dpkg: error processing libapache2-mod-php5 (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up apache2 (2.2.20-1ubuntu1.3) ...
Setting up mysql-server (5.1.66-0ubuntu0.11.10.2) ...
Setting up php5-mysql (5.3.6-13ubuntu3.9) ...
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jm-M2009:/home/jm#
```how to fix it ? :(
i'm sorry i'm new in using ubuntu...
thanks

---

### Post by wildmanne39 on 2012-11-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

