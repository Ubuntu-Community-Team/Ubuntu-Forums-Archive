---
title: "Simple Ubuntu 12.04 setup with no success, time sensitive"
date: 2012-07-19
forum: General Help
---

### Post by Caedis on 2012-07-19
[SIZE="3"]**Problem Description: **[/SIZE]I'm in the process of setting up a Moodle site on Ubuntu 12.04 i386. I've followed all the basic steps, and find that the moodle site is not comming up when I go to the moodle server at IPHERE/moodle.

I want to keep things simple so I'm installing the moodle from the repositories: 1.9.9.dfsg2-6

The system is purpose built for moodle and nothing more.

**The following commands have been issued since OS install:**

[LIST]
[*]sudo apt-get install clamav-daemon
[*]sudo tasksel   ----> Selected LAMP, created mysql root password
[*]Went to moodle server ip on seperate machine and recived the default page:

> [SIZE="4"]It works![/SIZE]

This is the default web page for this server.

The web server software is running but no content has been added, yet.

[*]sudo apt-get install moodle  ---> Configured application password, recived warning about no hostname, so binding to 127.0.1.1
[*]On other computer went to moodle server at IPHERE/moodle, recived the following:

> [SIZE="4"]Not Found[/SIZE]

The requested URL /moodle was not found on this server.

Apache/2.2.22 (Ubuntu) Server at IPHERE Port 80
[/LIST]

**The following is the output of the Moodle install:**

> user@moodle-server:~$ sudo apt-get install moodle
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following extra packages will be installed:
aspell aspell-en dbconfig-common dictionaries-common fontconfig-config javascript-common libaspell15 libfontconfig1 libgd2-xpm libjpeg-turbo8 libjpeg8 libjs-yui
libphp-magpierss libphp-pclzip libphp-snoopy libt1-5 libxpm4 mimetex php-fpdf php5-curl php5-gd php5-ldap php5-xmlrpc smarty ttf-dejavu-core unzip wwwconfig-common zip
Suggested packages:
aspell-doc spellutils ispell emacsen-common jed-extra libgd-tools ttf2pt1 postgresql-client
The following NEW packages will be installed:
aspell aspell-en dbconfig-common dictionaries-common fontconfig-config javascript-common libaspell15 libfontconfig1 libgd2-xpm libjpeg-turbo8 libjpeg8 libjs-yui
libphp-magpierss libphp-pclzip libphp-snoopy libt1-5 libxpm4 mimetex moodle php-fpdf php5-curl php5-gd php5-ldap php5-xmlrpc smarty ttf-dejavu-core unzip wwwconfig-common
zip
0 upgraded, 29 newly installed, 0 to remove and 2 not upgraded.
Need to get 16.7 MB of archives.
After this operation, 68.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main ttf-dejavu-core all 2.33-2ubuntu1 [1,552 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main fontconfig-config all 2.8.0-3ubuntu9 [44.4 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libfontconfig1 i386 2.8.0-3ubuntu9 [125 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libjpeg-turbo8 i386 1.1.90+svn733-0ubuntu4 [117 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libjpeg8 i386 8c-2ubuntu7 [2,112 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libxpm4 i386 1:3.5.9-4 [37.4 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libgd2-xpm i386 2.0.36~rc1~dfsg-6ubuntu2 [201 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libt1-5 i386 5.1.2-3.4ubuntu1 [148 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main php5-gd i386 5.3.10-1ubuntu3.2 [37.5 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main php5-curl i386 5.3.10-1ubuntu3.2 [28.0 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main unzip i386 6.0-4ubuntu1 [178 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main zip i386 3.0-4 [256 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe smarty all 2.6.26-0.2ubuntu1 [202 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libjs-yui all 2.8.2r1~squeeze-1 [2,476 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libphp-snoopy all 1.2.4-2 [17.6 kB] 
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libphp-magpierss all 0.72-10 [28.9 kB] 
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dbconfig-common all 1.8.47 [458 kB] 
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe php-fpdf all 3:1.7.dfsg-1 [82.1 kB] 
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libphp-pclzip all 2.8.2-2 [40.2 kB] 
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe moodle all 1.9.9.dfsg2-6 [9,248 kB] 
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libaspell15 i386 0.60.7~20110707-1 [621 kB] 
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dictionaries-common all 1.12.1ubuntu2 [246 kB] 
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main aspell i386 0.60.7~20110707-1 [89.4 kB] 
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main aspell-en all 6.0-0-6ubuntu2 [250 kB] 
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe wwwconfig-common all 0.2.2 [18.0 kB] 
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe javascript-common all 8 [4,208 B] 
Get:27 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe mimetex i386 1.50-1.1 [142 kB] 
Get:28 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main php5-ldap i386 5.3.10-1ubuntu3.2 [18.5 kB] 
Get:29 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main php5-xmlrpc i386 5.3.10-1ubuntu3.2 [35.8 kB] 
Fetched 16.7 MB in 30s (547 kB/s) 
Preconfiguring packages ...
/tmp/moodle.config.109993: 36: .: Can't open /usr/share/dbconfig-common/dpkg/config
moodle failed to preconfigure, with exit status 2
Selecting previously unselected package ttf-dejavu-core.
(Reading database ... 28332 files and directories currently installed.)
Unpacking ttf-dejavu-core (from .../ttf-dejavu-core_2.33-2ubuntu1_all.deb) ...
Selecting previously unselected package fontconfig-config.
Unpacking fontconfig-config (from .../fontconfig-config_2.8.0-3ubuntu9_all.deb) ...
Selecting previously unselected package libfontconfig1.
Unpacking libfontconfig1 (from .../libfontconfig1_2.8.0-3ubuntu9_i386.deb) ...
Selecting previously unselected package libjpeg-turbo8.
Unpacking libjpeg-turbo8 (from .../libjpeg-turbo8_1.1.90+svn733-0ubuntu4_i386.deb) ...
Selecting previously unselected package libjpeg8.
Unpacking libjpeg8 (from .../libjpeg8_8c-2ubuntu7_i386.deb) ...
Selecting previously unselected package libxpm4.
Unpacking libxpm4 (from .../libxpm4_1%3a3.5.9-4_i386.deb) ...
Selecting previously unselected package libgd2-xpm.
Unpacking libgd2-xpm (from .../libgd2-xpm_2.0.36~rc1~dfsg-6ubuntu2_i386.deb) ...
Selecting previously unselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.1.2-3.4ubuntu1_i386.deb) ...
Selecting previously unselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.3.10-1ubuntu3.2_i386.deb) ...
Selecting previously unselected package php5-curl.
Unpacking php5-curl (from .../php5-curl_5.3.10-1ubuntu3.2_i386.deb) ...
Selecting previously unselected package unzip.
Unpacking unzip (from .../unzip_6.0-4ubuntu1_i386.deb) ...
Selecting previously unselected package zip.
Unpacking zip (from .../archives/zip_3.0-4_i386.deb) ...
Selecting previously unselected package smarty.
Unpacking smarty (from .../smarty_2.6.26-0.2ubuntu1_all.deb) ...
Selecting previously unselected package libjs-yui.
Unpacking libjs-yui (from .../libjs-yui_2.8.2r1~squeeze-1_all.deb) ...
Selecting previously unselected package libphp-snoopy.
Unpacking libphp-snoopy (from .../libphp-snoopy_1.2.4-2_all.deb) ...
Selecting previously unselected package libphp-magpierss.
Unpacking libphp-magpierss (from .../libphp-magpierss_0.72-10_all.deb) ...
Selecting previously unselected package dbconfig-common.
Unpacking dbconfig-common (from .../dbconfig-common_1.8.47_all.deb) ...
Selecting previously unselected package php-fpdf.
Unpacking php-fpdf (from .../php-fpdf_3%3a1.7.dfsg-1_all.deb) ...
Selecting previously unselected package libphp-pclzip.
Unpacking libphp-pclzip (from .../libphp-pclzip_2.8.2-2_all.deb) ...
Selecting previously unselected package moodle.
Unpacking moodle (from .../moodle_1.9.9.dfsg2-6_all.deb) ...
Selecting previously unselected package libaspell15.
Unpacking libaspell15 (from .../libaspell15_0.60.7~20110707-1_i386.deb) ...
Selecting previously unselected package dictionaries-common.
Unpacking dictionaries-common (from .../dictionaries-common_1.12.1ubuntu2_all.deb) ...
Adding 'diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common'
Selecting previously unselected package aspell.
Unpacking aspell (from .../aspell_0.60.7~20110707-1_i386.deb) ...
Selecting previously unselected package aspell-en.
Unpacking aspell-en (from .../aspell-en_6.0-0-6ubuntu2_all.deb) ...
Selecting previously unselected package wwwconfig-common.
Unpacking wwwconfig-common (from .../wwwconfig-common_0.2.2_all.deb) ...
Selecting previously unselected package javascript-common.
Unpacking javascript-common (from .../javascript-common_8_all.deb) ...
Selecting previously unselected package mimetex.
Unpacking mimetex (from .../mimetex_1.50-1.1_i386.deb) ...
Selecting previously unselected package php5-ldap.
Unpacking php5-ldap (from .../php5-ldap_5.3.10-1ubuntu3.2_i386.deb) ...
Selecting previously unselected package php5-xmlrpc.
Unpacking php5-xmlrpc (from .../php5-xmlrpc_5.3.10-1ubuntu3.2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for libapache2-mod-php5 ...
*** Reloading web server config apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName**
[ OK ]
Setting up ttf-dejavu-core (2.33-2ubuntu1) ...
Setting up fontconfig-config (2.8.0-3ubuntu9) ...
Setting up libfontconfig1 (2.8.0-3ubuntu9) ...
Setting up libjpeg-turbo8 (1.1.90+svn733-0ubuntu4) ...
Setting up libjpeg8 (8c-2ubuntu7) ...
Setting up libxpm4 (1:3.5.9-4) ...
Setting up libgd2-xpm (2.0.36~rc1~dfsg-6ubuntu2) ...
Setting up libt1-5 (5.1.2-3.4ubuntu1) ...
Setting up php5-gd (5.3.10-1ubuntu3.2) ...
Setting up php5-curl (5.3.10-1ubuntu3.2) ...
Setting up unzip (6.0-4ubuntu1) ...
Setting up zip (3.0-4) ...
Setting up smarty (2.6.26-0.2ubuntu1) ...
Setting up libjs-yui (2.8.2r1~squeeze-1) ...
Setting up libphp-snoopy (1.2.4-2) ...
Setting up libphp-magpierss (0.72-10) ...
Setting up dbconfig-common (1.8.47) ...

Creating config file /etc/dbconfig-common/config with new version
Setting up php-fpdf (3:1.7.dfsg-1) ...
Setting up libphp-pclzip (2.8.2-2) ...
Setting up moodle (1.9.9.dfsg2-6) ...
dbconfig-common: writing config to /etc/dbconfig-common/moodle.conf

Creating config file /etc/dbconfig-common/moodle.conf with new version
granting access to database moodle for moodle@localhost: success.
verifying access for moodle@localhost: success.
creating database moodle: success.
verifying database moodle exists: success.
dbconfig-common: flushing administrative password

Creating config file /etc/moodle/config.php with new version

Creating config file /etc/moodle/apache.conf with new version

Creating config file /etc/moodle/apache.vhost.conf with new version
Setting up libaspell15 (0.60.7~20110707-1) ...
Setting up dictionaries-common (1.12.1ubuntu2) ...
Setting up wwwconfig-common (0.2.2) ...
Setting up javascript-common (8) ...
Setting up mimetex (1.50-1.1) ...
Setting up php5-ldap (5.3.10-1ubuntu3.2) ...
Setting up php5-xmlrpc (5.3.10-1ubuntu3.2) ...
Processing triggers for dictionaries-common ...
aspell-autobuildhash: processing: en [en-common]
aspell-autobuildhash: processing: en [en-variant_0]
aspell-autobuildhash: processing: en [en-variant_1]
aspell-autobuildhash: processing: en [en-variant_2]
aspell-autobuildhash: processing: en [en_CA-w_accents-only]
aspell-autobuildhash: processing: en [en_CA-wo_accents-only]
aspell-autobuildhash: processing: en [en_GB-ise-w_accents-only]
aspell-autobuildhash: processing: en [en_GB-ise-wo_accents-only]
aspell-autobuildhash: processing: en [en_GB-ize-w_accents-only]
aspell-autobuildhash: processing: en [en_GB-ize-wo_accents-only]
aspell-autobuildhash: processing: en [en_US-w_accents-only]
aspell-autobuildhash: processing: en [en_US-wo_accents-only]
Setting up aspell (0.60.7~20110707-1) ...
Processing triggers for dictionaries-common ...
Setting up aspell-en (6.0-0-6ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for dictionaries-common ...


---

### Post by dino99 on 2012-07-19
scroll the page down to get "moodle installation"  :P

[http://docs.moodle.org/20/en/Step-by-step_Installation_Guide_for_Ubuntu](http://docs.moodle.org/20/en/Step-by-step_Installation_Guide_for_Ubuntu)

or

[http://docs.moodle.org/23/en/Installation_on_Ubuntu_using_Git](http://docs.moodle.org/23/en/Installation_on_Ubuntu_using_Git)

---

### Post by Caedis on 2012-07-19
> **dino99 said:**
> scroll the page down to get "moodle installation"  :P

[http://docs.moodle.org/20/en/Step-by-step_Installation_Guide_for_Ubuntu](http://docs.moodle.org/20/en/Step-by-step_Installation_Guide_for_Ubuntu)

or

[http://docs.moodle.org/23/en/Installation_on_Ubuntu_using_Git](http://docs.moodle.org/23/en/Installation_on_Ubuntu_using_Git)

> Moodle installation

Install the Moodle package from the command-line interface and follow the prompts:
```
sudo apt-get install moodle
```
Database server software for Moodle: mysql-server -> follow remainder of instructions. Assuming the database is hosted on the same computer as the one Moodle is being installed upon, accept localhost for the options when prompted.
Edit Moodle configuration options (if needed):
```
sudo nano /etc/moodle/config.php
```
Edit Moodle apache2 configuration file (if needed):
```
sudo nano /etc/moodle/apache.conf
```
Finish installation through a web browser. (A server without a desktop will not have a web browser. Now you see why it is better to have an Ubuntu or Kubuntu desktop installed on top of the server). I recommend the unattended installation.
```
[http://localhost/moodle](http://localhost/moodle)
```

Thats the guide I followed to where I am now. 
> Edit Moodle configuration options *(if needed)*
```
<?php
 # This file has been generated by debconf
 # You can find a commented config file in /usr/share/doc/moodle/

 unset($CFG);
 $CFG = new stdClass();

 $CFG->dbtype = 'mysql';
 $CFG->dbhost = 'localhost';
 $CFG->dbname = 'moodle';
 $CFG->dbuser = 'moodle';
 $CFG->dbpass = 'xxxxxxxxxxxxxx';
 $CFG->prefix = 'mdl_';

 $CFG->wwwroot = 'http://localhost/moodle';
 $CFG->dirroot = '/usr/share/moodle';
 $CFG->dataroot = '/var/lib/moodle';
 $CFG->directorypermissions = 0750;
 $CFG->admin = 'admin';

 $CFG->pathtodu = '/usr/bin/du';
 $CFG->unzip = '/usr/bin/unzip';
 $CFG->zip = '/usr/bin/zip';

 $CFG->respectsessionsettings = true;

 # For improved security, make sure html purifier is used.
 $CFG->enablehtmlpurifier = true;

        if (file_exists("$CFG->dirroot/lib/setup.php"))  {       // Do not edit
                include_once("$CFG->dirroot/lib/setup.php");
        } else {
                if ($CFG->dirroot == dirname(__FILE__)) {
                        echo "<p>Could not find this file: $CFG->dirroot/lib/setup.php</p>";
                        echo "<p>Are you sure all your files have been uploaded?</p>";
                } else {
                        echo "<p>Error detected in config.php</p>";
                        echo "<p>Error in: \$CFG->dirroot = '$CFG->dirroot';</p>";
                        echo "<p>Try this: \$CFG->dirroot = '".dirname(__FILE__)."';</p>";
                }
                die;
        }
// MAKE SURE WHEN YOU EDIT THIS FILE THAT THERE ARE NO SPACES, BLANK LINES,
// RETURNS, OR ANYTHING ELSE AFTER THE TWO CHARACTERS ON THE NEXT LINE.
?>
```

> Edit Moodle apache2 configuration file *(if needed)*
```
 This file has been generated by debconf

#Uncomment the line below if you want to use alias
#This will not work well with virtual hosts
Alias /moodle /usr/share/moodle/

<DirectoryMatch /usr/share/moodle/>

Options +FollowSymLinks
AllowOverride None

order deny,allow
deny from all

allow from 127.0.0.0/255.0.0.0
allow from localhost
#comment out the line below to allow remote access
#allow from all

<IfModule mod_php5.c>
        php_flag magic_quotes_gpc Off
        php_flag magic_quotes_runtime Off
        php_flag file_uploads On
        php_flag short_open_tag On
        php_flag session.auto_start Off
        php_flag session.bug_compat_warn Off

        php_value upload_max_filesize 2M
        php_value post_max_size 2M
</IfModule>

<IfModule mod_dir.c>
        DirectoryIndex index.php
</IfModule>

</DirectoryMatch>

```

I go to these files and find nothing jumping out at me as needing configuration.

As for git, like I said, I want to keep this install simple, as I will be replicating it again on a production system. Compiling binaries has always been way more work than it's worth when we have perfectly good repos. (This isint FreeBSD, thankfully)

---

