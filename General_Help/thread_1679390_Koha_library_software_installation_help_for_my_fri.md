---
title: "Koha library software installation help for my friends"
date: 2011-01-31
forum: General Help
---

### Post by Rakeshvijayan on 2011-01-31
BELIEVE THIS DOCUMENTATION AND FOLLOW AS ROOT IF CANT ABLE TO LOGIN AS ROOT PLEASE SET PASSWORD FOR ROOT FROM YOUR CURRENTLY LOGIN USER 

:guitar:PLEASE USE KARMIC 9.10 UBUNTU :lolflag:
**sudo su**

Update your system,

**sudo apt-get update ** 
 
Creating Koha system user
 
Open a Command Terminal and type following commands, 
 
**groupadd koha **
**useradd -g koha koha **  
 **sudo mkdir /build **
 **sudo chmod -R 777 /build **
 

Download Koha-3.00.06 package from [www.koha-community.org]("http://www.koha-community.org")
Extract the package by right click and select "Extract to". 
 
Copy Koha package to the folder /build

**mv koha-3.00.06 /build**
 
[COLOR=#000000][FONT=Arial]**Installation of dependencies**[/FONT][/COLOR]

[FONT=Arial]**sudo apt-get install zip unzip lamp-server^ yaz idzebra-2.0 dselect  **[/FONT]

[FONT=Arial]**cd /build/koha-3.00.06 **[/FONT]
[FONT=Arial]**sudo dpkg --set-selections <install_misc/ubuntu.packages **[/FONT]
[FONT=Arial]**sudo dselect **[/FONT]

**Installation of Perl dependencies**

**apt-get  install libmarc-crosswalk-dublincore-perl libhtml-scrubber-perl  libalgorithm-checkdigits-perl libbiblio-endnotestyle-perl **
**apt-get install libemail-date-perl libyaml-perl libjson-any-perl libxml-writer-perl libxml-sax-writer-perl **

We have to install certain dependecies using CPAN,

**sudo cpan**

Accept all default settings.

Enter the following command in the CPAN prompt,

**install HTTP:OAI IPC::Cmd Text::CSV::Encoded **
 **quit**
 
 
**Configuration of  UTF-8 in MySQL and Apache **
Enable UTF-8 at MySQL 
Open a Terminal and type following command, 
 
**sudo gedit /etc/mysql/my.cnf **
[Under the Basic settings section, add the following,] 
 
[FONT=Courier New]*# UTF-8 Defaults for Koha *[/FONT]
[FONT=Courier New]*init-connect='SET NAMES utf8' *[/FONT]
[FONT=Courier New]*character-set-server=utf8 *[/FONT]
[FONT=Courier New]*collation-server=utf8_general_ci *[/FONT]

Save the file and close the editor. 
UTF-8 encoding in Apache 
Open a terminal and type the following command, 
 
**gedit  /etc/apache2/conf.d/charset **
[Add the following two lines in] 
 
[FONT=Courier New]*AddCharset UTF-8 .utf8 *[/FONT]
[FONT=Courier New]*AddDefaultCharset UTF-8 *[/FONT]

Save the file and close the editor.
  
 Enter following command to set locale on Ubuntu
  
 **sudo update-locale LANG=en_IN.UTF-8 **
  
 Creation of MySQL Database for KOHA 
Open a terminal and login as root and enter following commands, 
 
**mysql -u root -p **
[enter mysql root password here] 
 
Then type,
 
**create database koha; **
**grant all privileges on koha.* to 'kohaadmin'@'localhost' identified by 'katikoan'; **
**flush privileges; **
**quit;**
  
 **Test to make sure the SAX Parser is setup correctly**
 ** cd koha-3.00.06**
 **sudo gedit /etc/perl/XML/SAX/ParserDetails.ini**
 Move these two lines to the end of the file:

*[XML::LibXML::SAX::Parser]*
*[http://xml.org/sax/features/namespaces=1](http://xml.org/sax/features/namespaces=1) *
Run the command again,
 **misc/sax_parser_print.pl**
 
**Setting environment variables **
 
**gedit /etc/bash.bashrc.local **
Add the following lines there, 
 
[FONT=Courier New]export KOHA_CONF=/etc/koha/koha-conf.xml [/FONT]
[FONT=Courier New]export PERL5LIB=/usr/share/koha/lib[/FONT]
 
Save and close the file. 

**Koha Installation **
 
Now KOHA can be installed by following commands: 
Enter into Koha folder 
 
**cd /build/koha-3.00.06 **
**perl Makefile.PL **

Answer all questions  without any change. Default values are accepted for us. 
 
Type the following commands, 
 
**make **
**make test **
**sudo make install **
 
Add the following lines to /etc/apache2/ports.conf, just below the following line Listen 80 
Open a Command Terminal and type following commands 

 
**sudo gedit /etc/apache2/ports.conf **
 
[FONT=Courier New]Listen 8000 [/FONT]
[FONT=Courier New]Listen 8001[/FONT]
 
save the file and close.
 
Open a terminal and login as root 
sudo su
**ln -s /etc/koha/koha-httpd.conf /etc/apache2/sites-available/koha **
**sudo a2enmod rewrite **
**sudo a2ensite koha **
**/etc/init.d/apache2 restart **
 
  
**Zebra configuration **
Open a terminal and login as root 

**sudo ln -s /usr/share/koha/bin/koha-zebra-ctl.sh /etc/init.d/koha-zebra-daemon **
**sudo update-rc.d koha-zebra-daemon defaults **
**sudo ln -s /usr/share/koha/bin/koha-zebraqueue-ctl.sh /etc/init.d/koha-zebraqueue-daemon **
**sudo update-rc.d koha-zebraqueue-daemon defaults **
  
 Edit the following files,
  
 **sudo gedit /usr/share/koha/bin/koha-zebra-ctl.sh**
 **sudo gedit /usr/share/koha/bin/koha-zebraqueue-ctl.sh**
  
 Change USER and GROUP to root. Result is,
 [FONT=Courier New]#!/bin/bash[/FONT]
[FONT=Courier New]USER=root[/FONT]
[FONT=Courier New]GROUP=root[/FONT]
  
 Set following folders ownership to Koha user
  
 **sudo chmod -R 777 /var/lock/koha**
**sudo chown -R koha:koha /var/lock/koha**
**sudo chmod -R 777 /var/lib/koha/**
**sudo chown -R koha:koha /var/lib/koha **

**Cronjob Settings **
 **sudo su**
**cd /usr/share/koha/bin/cronjobs **
**crontab -u root crontab.example **
**crontab -u** username** crontab.example  **[Username denotes name of your home user]
**crontab -e **
 
Change the locations in following lines ,
 
*[FONT=Courier New]#Environment [/FONT]*
*[FONT=Courier New]PERL5LIB=/usr/share/koha/lib [/FONT]*
*[FONT=Courier New]KOHA_CONF=/etc/koha/koha-conf.xml [/FONT]*
 
[FONT=Courier New]#Some additional variables [/FONT]
[FONT=Courier New]KOHA_CRON_PATH=/usr/share/koha/bin/cronjobs[/FONT]
 
Save the file by pressing ctrl+o buttons 
Press enter 
Quit the editor by pressing ctrl+X buttons

Some settings for Apaache,

**sudo gedit /etc/koha/koha-httpd.conf**

Find the following line,

[FONT=Courier New]## OPAC[/FONT]
[FONT=Courier New]<VirtualHost 127.0.1.1:80>[/FONT]

Change the port number

[FONT=Courier New]## OPAC[/FONT]
[FONT=Courier New]<VirtualHost *:8001>[/FONT]

Find this line too,

[FONT=Courier New]## Intranet[/FONT]
[FONT=Courier New]<VirtualHost 127.0.1.1:8080>[/FONT]

Change to 

[FONT=Courier New]## Intranet[/FONT]
[FONT=Courier New]<VirtualHost 127.0.0.1:8000>[/FONT]

Add the following line at the end of the file,

**ServerName localhost**

Restart the Apaches server,

**sudo /etc/init.d/apache2 restart**

Run the Web installer  
 
[http://127.0.0.1:8000]("http://127.0.0.1:8000/")
 
URL of OPAC is [http://127.0.0.1:8001]("http://127.0.0.1:8001/")
 

**Zebra Management **
 
Starting Zebra Server 
 
Open a terminal and type following commands, 
 
**sudo su**
**sudo /etc/init.d/koha-zebra-daemon start**
** sudo /etc/init.d/koha-zebraqueue-daemon start**
 
Rebuilding Zebra Index 
**sudo  KOHA_CONF=/etc/koha/koha-conf.xml  PERL5LIB=/usr/share/koha/lib    /usr/share/koha/bin/migration_tools/rebuild_zebra.pl -b -r -v**

Quick Indexing
**sudo KOHA_CONF=/etc/koha/koha-conf.xml  PERL5LIB=/usr/share/koha/lib   /usr/share/koha/bin/migration_tools/rebuild_zebra.pl**** -b -w**


                                            ):P

---

### Post by svance1947 on 2011-11-05
Got as far as Koha installation, then received the following error:

vance@vance-acer:/build/koha-3.06$ sudo perl Makefile.PL
[sudo] password for vance: 
Can't locate ZOOM.pm in @INC (@INC contains: /build/koha-3.06 /etc/perl /usr/local/lib/perl/5.12.4 /usr/local/share/perl/5.12.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.12 /usr/share/perl/5.12 /usr/local/lib/site_perl .) at /build/koha-3.06/C4/Context.pm line 85.
BEGIN failed--compilation aborted at /build/koha-3.06/C4/Context.pm line 85.
Compilation failed in require at /build/koha-3.06/C4/Installer.pm line 24.
BEGIN failed--compilation aborted at /build/koha-3.06/C4/Installer.pm line 24.
Compilation failed in require at Makefile.PL line 31.
BEGIN failed--compilation aborted at Makefile.PL line 31.
vance@vance-acer:/build/koha-3.06$

---

