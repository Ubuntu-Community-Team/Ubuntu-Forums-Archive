---
title: "uploading files to LAMP on UBUNTU Desktop"
date: 2012-10-13
forum: General Help
---

### Post by shelac on 2012-10-13
My apologies if this would best belong somewhere else but I decided to dive in.
   
  I have an older computer that I thought that I would try to put to work as a developmental server.  I have no experience with LINUX but had the notion that I would get my feet wet by downloading and installing UBUNTU 12.04 (Desktop) on it.  That worked flawlessly.  I then installed LAMP with a few hurdles of my own making, but eventually got it working and parked a few PHP files in the var/www directory and was able to access them there.  I hardwired the machine to my Linksys Wireless router and can view the files from other Windows machines on the network.
   
  My next objective was to attempt to sort out how I would be able to upload files to the Apache server on UBUNTU using something like Filezilla or preferably directly from Dreamweaver on a Windows 7 laptop.
   
  I was optimistic when I saw the line “[COLOR=black][FONT=&quot]Connection established, waiting for welcome message...[/FONT][/COLOR][COLOR=black][FONT=&quot]’ in the Filezilla log, but I have hit a dead end.  [/FONT][/COLOR]
   
  [COLOR=black][FONT=&quot]Status:              Connecting to 192.168.1.105:80...[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]Status:              Connection established, waiting for welcome message...[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Error:                 Connection timed out[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Error:                 Could not connect to server[/FONT][/COLOR]
   
  I have tried the sudo user name as well as “root” for a user name.
   
  I installed webmin thinking that this might bring me closer to discovering the solution.  I am clearly out of my league here.  Does anyone have any advice for me as to what I need to install or how I need to configure what I have to achieve the desired results?
   
  Thanks for your help.

---

### Post by Wim Sturkenboom on 2012-10-13
> 
Status: Connecting to 192.168.1.105:**[COLOR="Red"]80[/COLOR]**...

Why 80? That indicates that you're trying to connect to apache.

Do you have a FTP server (daemon) running? You use a ftp client to connect to a ftp server (daemon), not to a web server (daemon).

If you haven't done so, install e.g. vsftpd

---

### Post by shelac on 2012-10-13
Thanks for the quick response.  I confess that I am completely clueless when it comes to this stuff.    But you have to start somewhere.  I came to the erroneous conclusion that I would want to connect to Apache.
   
  I will install vsftpd 
   
  What port should I be using then?

---

### Post by shelac on 2012-10-13
Thanks again.  Somewhere I read that it is Port 21 and it worked.  Now it is a matter of learning how to edit some files, change permissions, etc. so that I can upload files and create directories.

---

### Post by Wim Sturkenboom on 2012-10-14
Great, please mark your thread as solved using the thread tools just above the first post on this page.

I never use /var/www; my web directories are in the user's home directory. This is an approach from long ago where I did not want to fight with permissions. Just a matter of changing the '*document root*' in the apache configuration ;) Only disadvantage is that apache can't write there but not everybody has a need for that and it can be solved by having a dedicated subdirectory where apache can write.

---

### Post by shelac on 2012-10-14
I appreciate your comment about fighting with permissions.
   
  I bumbled around for a couple of hours last evening trying to get it set up so that I could create a directory and upload files to var/www.  No success yet.  Downloading files behaves.
   
  I changed the vsftpd.conf file to allow creating directories but no combination of permissions that I tried would yield the results.  It was set up for anonymous and I even tired changing that with no luck.  And in my case it amounts to luck as I clearly don’t know what I’m doing.  I have changed so many settings now that I will probably uninstall the whole thing to get back to equilibrium and start over.
   
  I decided to walk away from it for a while and perhaps I will get an inspiration.
   
  I would be the exclusive user of this developmental server and it is living on my home wireless router so I am thinking that security is not a major concern here.
   
  Thanks again.

---

### Post by shelac on 2012-10-18
I thought that I would leave this open until I had a chance to try to play with the ownership and permissions to determine if I could sort this out by myself.

So far no success.  Luck might be a better word as I clearly am clearly bumbling around in an attempt to have a solution revealed to me.

While using Filezilla I am able to see the files that are parked in /var/www but I still can’t create a directory, rename or upload a file to it.

Here is the way that vsftpd.conf is set up:

# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem

Here is the current permissions and ownership for the /var/www directory.

ray@ray-desktop:/var$ ls -la
total 56

drwxr-xr-x  2 ray  root     4096 Oct 15 22:45 www

And the permissions and ownership for the /etc/apache2 directory.

ray@ray-desktop:/etc$ ls -la
total 1164

drwxr-xr-x   7 root root    4096 Oct 15 21:33 apache2

 
I have done a restrart on both the vsftpd and Apacche2.

I didn’t have a lot of ideas in the first place and now I have none.  Any guidance would be greatly appreciated.

---

### Post by Wim Sturkenboom on 2012-10-19
That's exactly why I use a different approach ;)

You can make yourself a member of the www group. I think that that would solve the permission issue.

There is another problem with your setup. Using ftp, you can access your full file system which is dangerous. I know that you're only 'playing', but you should get in the habit of securing it from the start. The change that should be made in the vsftpd.conf is to remove the '#' at the beginning of the line in red.

```

[COLOR="Red"]#chroot_local_user=YES[/COLOR]
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list

```
This will jail users to their home directory so they can't snoop around and mess up. The implication is that you can't get to /var/www; maybe a symlink in your home directory to /var/www will work (other can advise).

---

### Post by shelac on 2012-10-20
I have read a number of items on the Internet relating to ownership and permissions.  Most of it makes sense but there are obviously lots that is eluding me.
   
  The vsftpd utility is currently set up for anonymous user.  I tried logging through Filezilla using my UBUNTU user name and password it is successful in getting me to a file system that isn’t helpful.  Empty directories.  So I am no further ahead.
   
  This may be the dumbest question ever, but when you suggest that I should make myself a member of the /var/www group does that mean I should set up an “anonymous” user in UBUNTU?
   
  Sorry to be so dense about this and thanks for your patience.  I don’t even know what questions to ask!

---

### Post by Wim Sturkenboom on 2012-10-21
I did misread your post #7; you've made yourself the owner of /var/www. So forget my comment about making yourself a member of the group www (which should actually be www-data).
```

ray@ray-desktop:/var$ ls -la
total 56

drwxr-xr-x 2 ray root 4096 Oct 15 22:45 www

```
That's not really the intention but should do the trick mostly. Below my approach (with sufficient detail, I hope).

Regarding vsftpd, anonymous login will not get you anywhere with regards to /var/www. Below is my vsftpd.conf that disables anonymous login and enables normal login. The version of vsftpd that comes with 12.04 gave me a hard time but this is tested and working; if you're using an older version of Ubuntu, you might not need the stuff at the end. When you ftp to the server and login with your ubuntu username and password (on the server), you will be taken to your home directory. Note that you need root privileges (so prepend commands with sudo (terminal) or gksudo graphical environment).

```

# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
#WimS
#anonymous_enable=YES
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
#WimS
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
#WimS
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem

#WimS
# to prevent the problem of "500 OOPS: vsftpd: refusing to run with writable root inside chroot()" after login as normal user
#http://www.benscobie.com/fixing-500-oops-vsftpd-refusing-to-run-with-writable-root-inside-chroot/
# allow_writeable_root=YES does not work !!
# this makes the root directory /home instead of /home/user
#local_root=/home
# don't forget to change the user's homedir in /etc/password to e.g.
#  /home/./wim
passwd_chroot_enable=YES

```

You need to make a modification to your /etc/password for every user that needs ftp access (not something that I prefer to do, but there is no other way). I've created a testuser; you need to find your user in that file. The first line below shows the original one, the second line the modified one. Again, root privileges are required to modify the file.
```

[s]testuser:x:1001:1001:testuser,,,:/home/testuser:/bin/bash[/s]
testuser:x:1001:1001:testuser,,,:/home/./testuser:/bin/bash

```
Any user that you forget will see the follwoing after ftp login
```

500 OOPS: vsftpd: refusing to run with writable root inside chroot()

```

Next create a directory for your website in your home directory; no root privileges required.
```

testuser@VirtualBox:~$ mkdir website1
testuser@VirtualBox:~$ mkdir website1/www
testuser@VirtualBox:~$ ls -l website1/
total 4
drwxrwxr-x 2 wim wim 4096 Oct 21 10:43 www
testuser@VirtualBox:~$ 

```

Last step is to let apache use this directory instead of /var/www. For this you need to modify [s]/etc/apache/sites-available/[/s] /etc/apache/sites-available/default and replace any reference to /var/www by /home/yourusername/website1/www. Again root privileges required.

This is the contents of the file on my (fresh system). In red the changes; I commented out the original line by putting a '#' in front of it and added the new line.

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

[COLOR="Red"]	DocumentRoot /home/testuser/website1/www[/COLOR]
[COLOR="Red"]#	DocumentRoot /var/www[/COLOR]
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
[COLOR="Red"]	<Directory /home/testuser/website1/www>[/COLOR]
[COLOR="Red"]#	<Directory /var/www/>[/COLOR]
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Next you can restart apache
```

wim@VirtualBox:~/website1/www$ sudo service apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
wim@VirtualBox:~/website1/www$ 

```
You can ignore the warnings and test the changes by navigating to your server using a webbrowser. As there's currently nothing in the new documentroot, you will get an empty directory listing. If you now copy /var/www/index.html to /home/yourusername/website1/www and after refreshing the page in the browser, you should see the 'it works' page.

//EDIT
make backups of any files that you modify !!

---

### Post by Wim Sturkenboom on 2012-10-21
A note on the changes in the apache configuration. The documentroot is where apache looks for files for the website. So that was the first change in that file.

The second change is due to the first change as we have to tell apache what can be done with that directory.

---

### Post by shelac on 2012-10-21
Your directions were great.  I was able to follow them step-by-step and the result was that I was finally able to see the files and folders in Filezilla, rename them, and upload to the folders.  I was smiling.
   
  Because it was already set up for it, I tested the tricks mentioned above while using Filezilla with the user name as the UBUNTU the super user “ray”.  However, when I attempted to browse to the location using Firefox, (/home/ray/website1/www)  I was unable to find the files that I had parked there.  404 error.
   
  I had substituted “rgc” for “testuser” in the examples that you provided and tried “/home/rgc/website1/www” in Firefox, confident that this would solve the problem and still got a 404 error.
   
  So I then returned to Filezilla and tried using it with the “rgc” user name which I had set up earlier in UBUNTU using the GUI but it didn’t ask for a password at the time and Filezilla wasn’t going to be happy without one.  A quick browse revealed how to add a password to an existing user.  Done! I tested the new “rgc” user and password.  It worked fine. 
   
  And I think that there is where the train went off the rails.  Now Filezilla fails to connect to the UBUNTU server either as "rgc” or “ray”.  Big trouble.

   
  [COLOR=red][FONT=&quot]Error:                 Could not connect to server[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]Status:              Waiting to retry...[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]Status:              Connecting to 192.168.1.105:21...[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]Status:              Connection attempt failed with "ECONNREFUSED - Connection refused by server".[/FONT][/COLOR]
  [COLOR=red][FONT=&quot]Error:                 Could not connect to server[/FONT][/COLOR]
   
  I think that the only change that I made was adding the “rgc” user password so I decided to try deleting that user ([FONT=Arial]sudo userdel[/FONT][FONT=&quot] rgc) [/FONT]to see if I could log in through Filezilla with that out of the way and using the “ray” super user password that had worked before.  No luck.
   
  So once again I created the user “rgc”  This time from the terminal.


```
sudo useradd -d /home/rgc -m rgc
  sudo passwd rgc

```  I thought that I should check the line in the /etc/passwd file to make sure that nothing had changed.  Still the same!
   
  ```
rgc:x:1001:1001:rgc,,,:/home/./rgc:/bin/bash
```  For good luck restarted both apache2 and vsftpd.config
   
  And the final measure was to reboot the UBUNTU machine.  Same results.  Can’t access the files through Filezilla.
   
  And I was so very close!
   
  Now I am out of ideas again.
   
  You folks who can tolerate the lack of knowledge from newbies like me are saints.  I really appreciate all the effort that you have contributed to helping me through this dilemma.  For someone who knows there way around UBUNTU this is probably a no-brainer.  I have learned a great deal through this process but would truly like to wrap this up and get on with the next chapter.  Thanks again.

---

### Post by Wim Sturkenboom on 2012-10-22
There was one initial mistake; you should not try to view /home/user/website1/www directly. Instead you should have tried 'the normal way' like [noparse]http://localhost[/noparse] or [noparse]http://192.168.1.105[/noparse].

Let's check if apache is still working locally and remotely. On your server, start a webbrowser and navigate to [noparse]http://localhost[/noparse]; do you get the page that you expect. Next try [noparse]http://192.168.1.105[/noparse] directly on the server. And next try it from your 'other' machine with [noparse]http://192.168.1.105[/noparse].

I don't know what's wrong with the ftp server; the first log to check is /var/log/vsftpd.log and see if it states why you can't connect. You might want to increase the verbosity of the log for this by adding the below line to vsftpd.conf (and next restarting the vsftpd server).

```

log_ftp_protocol=YES

```
Next in a terminal run
```

sudo tail -f /var/log/vsftpd.log

```
And from your remote machine connect and provide your credentials; it might be better if you use a command line ftp client (should be installed by default) so yu can see what happens step by step.

```

ftp 192.168.1.105

```

I will post some samples just now

---

### Post by Wim Sturkenboom on 2012-10-22
Using a Windows ftp client (Linux will be the same) using an invalid user
```

C:\Users\wsturkenboom>ftp 172.31.208.129
Connected to 172.31.208.129.
220 (vsFTPd 2.2.2)
User (172.31.208.129:(none)): abc
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> bye
221 Goodbye.

```
The corresponding result in the vsftpd.log
```

Mon Oct 22 14:11:40 2012 [pid 2675] CONNECT: Client "172.31.208.36"
Mon Oct 22 14:11:40 2012 [pid 2675] FTP response: Client "172.31.208.36", "220 (vsFTPd 2.2.2)"
Mon Oct 22 14:11:43 2012 [pid 2675] FTP command: Client "172.31.208.36", "USER abc"
Mon Oct 22 14:11:43 2012 [pid 2675] [abc] FTP response: Client "172.31.208.36", "331 Please specify the password."
Mon Oct 22 14:11:45 2012 [pid 2675] [abc] FTP command: Client "172.31.208.36", "PASS <password>"
Mon Oct 22 14:11:47 2012 [pid 2674] [abc] FAIL LOGIN: Client "172.31.208.36"
Mon Oct 22 14:11:48 2012 [pid 2675] [abc] FTP response: Client "172.31.208.36", "530 Login incorrect."
Mon Oct 22 14:11:53 2012 [pid 2675] FTP command: Client "172.31.208.36", "QUIT"
Mon Oct 22 14:11:53 2012 [pid 2675] FTP response: Client "172.31.208.36", "221 Goodbye."

```

Using a Windows ftp client (Linux will be the same) using a valid user
```

C:\Users\wsturkenboom>ftp 172.31.208.129
Connected to 172.31.208.129.
220 (vsFTPd 2.2.2)
User (172.31.208.129:(none)): wim
331 Please specify the password.
Password:
230 Login successful.
ftp> bye
221 Goodbye.

```
The corresponding result in the vsftpd.log
```

Mon Oct 22 14:11:54 2012 [pid 2677] CONNECT: Client "172.31.208.36"
Mon Oct 22 14:11:54 2012 [pid 2677] FTP response: Client "172.31.208.36", "220 (vsFTPd 2.2.2)"
Mon Oct 22 14:11:56 2012 [pid 2677] FTP command: Client "172.31.208.36", "USER wim"
Mon Oct 22 14:11:56 2012 [pid 2677] [wim] FTP response: Client "172.31.208.36", "331 Please specify the password."
Mon Oct 22 14:12:00 2012 [pid 2677] [wim] FTP command: Client "172.31.208.36", "PASS <password>"
Mon Oct 22 14:12:00 2012 [pid 2676] [wim] OK LOGIN: Client "172.31.208.36"
Mon Oct 22 14:12:00 2012 [pid 2678] [wim] FTP response: Client "172.31.208.36", "230 Login successful."
Mon Oct 22 14:12:08 2012 [pid 2678] [wim] FTP command: Client "172.31.208.36", "QUIT"
Mon Oct 22 14:12:08 2012 [pid 2678] [wim] FTP response: Client "172.31.208.36", "221 Goodbye."

```

Note: you can stop the tail by pressing <ctrl>C. And leave the ftp client by typing bye and pressing <enter> (as shown).

PS
Tested on a 10.04 system, not 12.04. But I don't expect differences (said the optimist ;))

---

### Post by shelac on 2012-10-22
Thanks for sticking with me on this.
   
  I can now again connect to the server using Filezilla and the “rgc” user and password.  Hurray!
   
  It dawned on me that I may not have switched the ownership of the files back to “root” after making the changes.  I have now made sure that the /etc/passwd, /etc/vsftpd.conf, and /etc/apache2/sites-available/default files are all owned by root.  So now at least I think that I am back on more stable ground.  My apologies for that oversight.
   
  Filezilla presents me with a root of “rgc” and a list of empty folders.  Desktop, Documents, Downloads, Music, Pictures, Public, Templates, Videos and a file named examples.desktop.  I can create a new folder, upload a file to it and change the name.
   
  However I still can’t find it from a remote browser.
   
  I am able to access phpmyadmim from the UBUNTU machine.  I don’t recall noticing that there was a double “localhost” on the tab before, but there is obviously a great deal that eludes me.
   
  /localhost/localhost|phpmyadmin 3.4.10.1 deb 1
   
  [http://localhost/phpmyadmin/index.php?token=c512bcea14d8b9a608a99d50cec36d2a#PMAURL:server=1&target=main.php&token=c512bcea14d8b9a608a99d50cec36d2a](http://localhost/phpmyadmin/index.php?token=c512bcea14d8b9a608a99d50cec36d2a#PMAURL:server=1&target=main.php&token=c512bcea14d8b9a608a99d50cec36d2a)
   
  So it seems to me that the Apache server is working.
   
  Now if I could just find the files with my remote browser.
   
  I have tried everything in the path [http://192.168.1.105/home/rgc/website1/www](http://192.168.1.105/home/rgc/website1/www) and always get 404’s.
   
  Thanks again.  Your instructions are terrific and the detail helps me a great deal.

---

### Post by Wim Sturkenboom on 2012-10-22
OK

I made a mistake in my post #10; you need to modify /etc/apache/sites-available/default, not /etc/apache/sites-available/ (which is a directory). [COLOR="Blue"]Did you try to make those changes?[/COLOR]

Assuming phpmyadmin was installed before post #10, the suggested changes to the apache configuration did not take effect or you did not make them. If the changes would have taken effect, phpadmin would have 'disappeared' from your browser.

So I think apache is still looking at /var/www.

Please post the output of 
```

sudo ls -l /var/www

```
I'm quite sure we'll find phpmyadmin in there; [COLOR="Blue"]please confirm[/COLOR].

And a little note on how apache works. It 'translates' a request for a webpage (e.g. [noparse]http://localhost/index.html[/noparse]) to a request for a file on your server. In the original configuration, a request for [noparse]http://localhost/somepage.html[/noparse] will be translated for a request for /var/www/somepage.html. And after the modification that I described, it would be translated to a request for /home/rgc/website1/www/somepage.html

So there is no need (and it will not work) to do [noparse]http://localhost/home/rgc/website1/www[/noparse]; it should just be [noparse]http:/localhost[/noparse] to present the pages somewhere in your home directory.

Note:
after the changes you will loose phpmyadmin; a hurdle that we can take later. So don't panic ;) And don't forget to restart apache2

---

### Post by shelac on 2012-10-22
Eureka!
   
  The good news is that I am now able to find the files with the remote browser.
   
  The bad news is that I wasted a bunch of your time.  Your directions were explicit, but inadvertently I managed to overlook a critical step in that I did not log out of the user “ray” and log in again as the user ”rgc” when I created the /website1/www folder.
   
  I’m not sure what I was thinking.  Probably nothing at all or that it had something to do with the way that UBUNTU isolates each user.  No common files available among users?  Lesson learned.  You gave me enough clues that thought that I had best do some investigative backtracking.
   
  I still evidently have some permission issues.  I can view the two test type files that I copied from the /var/www folder and pasted into the rgc/website1/www folder but for some reason (permissions matter I expect) I get a “Forbidden - You don't have permission to access /index.html on this server.”  on a file that I copied from my remote laptop using Filezilla.
   
  I renamed the original index.html file to index_orig.html and it still loads.
   
  If you have any advice as to what is going on here and help to deal with the phpmyadmin matter I think that I will be able to finally tag this as solved and sign off in deep gratitude.  With your patience and help I have learned a lot about UBUNTU.  As you have no doubt realized I am one of those folks who know just enough to be dangerous and a great deal of the appeal is enjoying the opportunity to work with people like you in the UBUNTU family.

---

### Post by shelac on 2012-10-22
I thought that the time had come to learn a bit about permissions and investigate the attributes of the** [COLOR=DarkSlateBlue]_files that would loa_d[/COLOR]**;
   
  Owner – Read Write
  Group (rgc) – Read only
  Others – Read only
   
  The permissions of the files that _**[COLOR=Navy]would not load[/COLOR]**_ were:
   
  Owner – Read Write
  Group (rgc) - none
  Others – none
   
  I changed the permissions to 664  or  ( - r w – r w – r - )   on these and was able to load them.
   
  Is there a method available that I could invoke so that I would not have to manually change the permissions on anything that I move into the /www folder while using Filezilla or Dreamweaver?
   
  Along with the new index file that I moved into the /www folder I also moved folders names “images” and “styles from the rest of the project.
   
  These folders permissions are ( d r w x - - - - - - - )
   
  And the files in them are     ( – r w - - - - - - - )
   
  The /www folder is     ( d r w x r w r – x )  (owner rgc)
   
  The /website1 folder is the same.
   
  My goal would be to be able to move/locate them on the Apache2 server and behave like they do on the Windows 7 laptop.

Thanks - as always.

---

### Post by Wim Sturkenboom on 2012-10-23
The permission settings for uploads are defined in the vsftpd.conf file
```

# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
[COLOR="Red"]#local_umask=022[/COLOR]

```
Remove the '#' at the beginning of the red line so it's no longer treated as a comment and restart your vsftpd server. Note that the umask is the inverse of the permissions that you want (so 077 results in 700 and 022 results in 755).

Directories created using ftp will now have _drwxr-xr-x_ and files will have _-rw-r--r--_.

That should round it up. I just like to make you aware of one little problem that you might encounter one day; apache will not be able to write in your directories; most users don't have a need for that, but if your web application includes e.g. an image upload facility for visitors, this will be an issue. I use a dedicated directory for it where apache has permission to write.

I will add one more post to explain why I use /home/rgc/website1/www

---

### Post by Wim Sturkenboom on 2012-10-23
Note in advance
I'm not trying to force you into any direction setting up your server. This just explains my approach.

This is my setup on an intranet server
```

websites/
|-- [drwxr-xr-x wim      users   ]  assetregister
|   |-- [drwxr-xr-x wim      users   ]  inc
|   `-- [drwxr-xr-x wim      users   ]  web
|       `-- [drwxrwxr-x wim      users   ]  files
...
...
...
|-- [drwxr-xr-x wim      users   ]  porepo
|   |-- [drwxr-xr-x wim      users   ]  inc
|   `-- [drwxr-xr-x wim      users   ]  web
|       |-- [drwxrwxr-x wim      users   ]  files
|       `-- [drwxr-xr-x wim      users   ]  images
...
...
...

```
In my home directory, I have a subdirectory 'websites' that contain the different websites; shown above are two of them (assetregister and porepo).

**1)**
Each has a 'web' directory (yours was www) and an 'inc' directory. The 'web' directory is from what pages are served (the document root) by apache to the visitors of the website. The 'inc' directory is not accessible by visitors of the website but apache can read there.
This allows to store files in there that contain secure information. I have e.g. a file connect.php in there with a function to connect to a mysql database that contains username and password. In a php page in the 'web' directory, I include that file and call that function.

As the 'inc' directory is not accessible to the visitors, the login credentials for the mysql server are secure.

The second purpose for this directory is to store files with php functions that can be re-used by different web pages on the site (write once, use often ;))

**2)**
In each 'web' directory I have a subdirectory 'files' where I allow apache to write.

```

wim@webserver:~/websites/porepo/web$ ls -ld files
drwxrwxr-x+ 2 wim users 274432 2012-10-22 15:38 files/

```
Looks quite normal and does not show that anybody but wim can write there. But note the + at the end of the permissions. This + shows when ACL (access control list) is used to set additional permissions.
```

wim@webserver:~/websites/porepo/web$ getfacl files
# file: files
# owner: wim
# group: users
user::rwx
user:apache:rwx
group::r-x
mask::rwx
other::r-x

```
From this we can see all permissions and it is clear that the user apache can do everything in that directory.
You can set those permissions using
```

setfacl -m u:apache:rwx files

```

Note:
This is a Slackware server and the webserver daemon (httpd) runs as the user apache; you need to check which user runs httpd on your system; it's probably www-data (but I'm not sure).


Good luck

---

### Post by shelac on 2012-10-23
Everything seems to be working very nicely thanks to your patience and dedication.  I was able to use Filezilla to copy a number of files to the UBUNTU server and do all the tricks with them.  
   
  I do have a couple of questions though.
   
  I set up “rgc” as the “testuser” in the example that you provided.  I’m curious if I would do any damage if I altered the /etc/passwd file to add the super user “ray” to be able to access the server?  Not a necessity, just wondering.



```
ray:x:1001:1001:rgc,,,:/home/./ray:/bin/bash
```  Also in Post 16 you mentioned:
   
  > Note:
after the changes you will loose phpmyadmin; a hurdle that we can take later. So don't panicIs there something special that I will need to do to be able to access the phpmyadmin utility now?
   
  My education in making this all work has taken a long path and I am thrilled to be able to have a local developmental server available to play with.
   
  Now I just have to figure out how to set up Dreamweaver so that I can have it copy my work to the LAMP server.  I’m not there yet.

---

### Post by Wim Sturkenboom on 2012-10-24
You should be able to use your user 'ray' in ftp. But 'ray' will be locked to his home directory so can not access the files of user 'rgc'.

With regards to phpadmin, I assume that that is still installed in /var/www and therefore no longer accessible.

What I suggest is to configure (another) virtual hosts. To do so, make a copy of your /etc/apache2/sites-available/default

```

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/phpmyadmin

```
Next modify the phpmyadmin file that you just created. The below example is based on the very original default file, not the one you modified.

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

[COLOR="Red"]	ServerName phpmyadmin
	DocumentRoot /var/www/phpmyadmin
[/COLOR]	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
[COLOR="Red"]	<Directory /var/www/phpmyadmin/>
[/COLOR]		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
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

```

You also need to create an entry in /etc/hosts for this new website; add the red line below. You need root privileges to edit the file.

```

127.0.0.1	localhost
127.0.1.1	wim-desktop
[COLOR="Red"]127.0.0.1	phpmyadmin[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Next issue the following 2 commands; the first one enables the new site on your system and the second one is obvious (I guess)
```

sudo a2ensite phpmyadmin
sudo service apache2 restart

```

Next you can use a browser to access the sites
[noparse]http://localhost[/noparse] will give you the site that we created earlier (in your home directory)
[noparse]http://phpmyadmin[/noparse] will give you phpmyadmin located in /var/www/phpmyadmin.

PS
Virtual hosts is the normal way to allow one webserver to serve different websites (including different domains and subdomains).

---

### Post by shelac on 2012-10-26
Sorry for the delay in responding.  Sometimes life gets in the way.   Everything is behaving according to plan now.  I appreciate all that you have done for me.
   
  I have one last question and this may not be the place for it but it is on the same theme.  Sort of.
   
  I notice that sometimes when searching the Internet for documents, I will get a Directory listing of files and folders instead of an error message such as “File not found”  is this a setting on the server?
   
  Now I will figure out how to set this as “Solved”.  It has been a long haul but I am a bit smarter now.  Thanks.

---

### Post by Wim Sturkenboom on 2012-10-28
It was a pleasure.

> 
I notice that sometimes when searching the Internet for documents, I will get a Directory listing of files and folders instead of an error message such as &#8220;File not found&#8221; is this a setting on the server?

You have to elaborate a bit on what you exactly mean, but I guess it's a setting on the server or a dedicated error page that gives a directory listing

It might however be outside my league. There is a dedicated server section ( [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339) ) where your question might fit better. This thread was also started as a thread about uploading, so the title no longer covers the content and therefore might not attract the right people to answer ;)

Good luck

---

### Post by shelac on 2012-11-01
Just when I thought that everything was well in my world, I discovered another impediment to my progress.  It seems that Apache2 needs to have rights to create a file in my working folders.  And I suspect that it would also require rights to create a temp file wherever that should happen.  I haven’t figured out where that is yet since I have not been able to create one.  As always any ideas would be greatly appreciated, and thanks in advance.

---

### Post by Wim Sturkenboom on 2012-11-01
I was wondering when that question was coming ;) In post #20 I gave a possible solution with _setfacl_.

For your setup, a simple _chgrp_ might be easier to give write access.

```

wim@i3-2120:~$ ls -ld testdir/
drwxrwxr-x 2 wim wim 4096 Nov  1 17:49 testdir/
wim@i3-2120:~$ **[COLOR="Red"]sudo chgrp www-data testdir/[/COLOR]**
[sudo] password for wim: 
wim@i3-2120:~$ ls -ld testdir/
drwxrwxr-x 2 wim www-data 4096 Nov  1 17:49 testdir/
wim@i3-2120:~$ 

```
Replace testdir with the path to the document root. Make sure the group's permissions are rwx.

I'm not sure if this will take care of temporary files, but I have not had problems on my Slackware server with temporary files.

---

