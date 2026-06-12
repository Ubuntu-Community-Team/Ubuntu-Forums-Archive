---
title: "Proftpd"
date: 2012-01-27
forum: General Help
---

### Post by pkeeney on 2012-01-27
I have a few questions i hope someone can help me. I'm helping a friend set up a home server and Im trying to get ftp working right. I'm using ssh to connect to friends computer from my house, so everything im doing is by command. I got server up and running, installed SMF its working and now i just need to allow SMF to chmod files in the /var/www directory.

This is what i did-

Installed proftpd (sudo apt-get install proftpd) 

added user userftp (sudo useradd userftp -p my_password -d /var/www -s /bin/false)

set password for userftp (sudo passwd userftp)

added /bin/false to the /bin/shells file

Thanks for any help 

Im able to log in using FileZilla using userftp and password but for some reason I cant chmod. Im using Webmin to edit the proftpd.conf file tried different thing from the proftpd website.
The main error im seeing when trying to chmod -Operation not permitted

How do i permit proftpd user (userftp) chmod privileges?

---

### Post by pkeeney on 2012-01-28
Can someone help me put this to rest so i can move on to the next thing.
Thanks

---

### Post by cryptotheslow on 2012-01-28
Are you trying to chmod files in /var/www ?

Check the directory and file permissions for there if so. This sounds more like an underlying permissions issue rather than anything to do with proftpd - remember proftpd cannot overrule existing file permissions.

Sorry if that sounds a bit vague - but I don't know what you are referring to with "SMF" to be any more specific.

---

### Post by pkeeney on 2012-01-28
SMF is System Machines Forum and Im trying to give SMF privileges to chmod files by using proftp.

SMf uses a php ftp client to handle the permissions on its own files. There is several plugins and mods that need to write to different files (example theme files) so i need to chmod these files to 777 and then back to 755 or 644 instead of me doing that manually i can let SMF handle that using ftp. To me its no big deal do this manually but this is my friends forum and he is not good with computers.

So guess what im trying to do is give user and or proftp rights to chmod files in the /var/www directory.

If that is not possible what ftp server should i use?


Thanks

---

### Post by cryptotheslow on 2012-01-28
Yes it should be possible. Who owns the files in /var/www ?

```
ls -l /var/www
```** EDIT TO ADD:-Thinking about this some more - maybe the ftpuser needs some kind of shell (not /bin/false) to be able to chmod? I have proftpd running on one of my boxes so am going to test the theory now.

*** EDIT AGAIN: Scrap the theory about shells - I can chmod fine via ftp when the user has /bin/false (or /bin/sh for that matter)


How about (for testing purposes) change your ftpuser to have /bin/sh and su to it and try to chmod the files from the command line as that user - that might give you some more relevant error message to troubleshoot with.


**** LAST EDIT I PROMISE :) **** I just chown'd a file to a different user on the ftp server and tried chmod'ing it over ftp and replicated your "-Operation not permitted" message. So I'm sticking with my original thought - it's file permissions preventing the chmod. You (as in the ftpuser) needs to own the file (or have elevated privilege) to be able to chmod it.

---

### Post by Lars Noodén on 2012-01-28
Let's take a few steps back.  You write that you have SSH up and running.  That means that you already have SFTP available and that can do **chmod** as one of its built-in functions.  Also, unlike [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/), it is [secure](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  

If you want to lock it down so that SFTP is allowed but shell access is not, then you can use the [ForceCommand](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) directive in [font=Courier New]sshd_config[/font].  The following locks members of the group 'webmasters' into only SFTP:

```

Subsystem sftp internal-sftp

Match Group webmasters
        ForceCommand internal-sftp

```

Then set the permissions for [font=Courier New]/var/www[/font] so that the group 'webmasters' can write to it:

```

# create group
sudo addgroup webmasters

# add a user to the group
sudo gpasswd --add pkeeney  webmasters


# set directory permissions
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

---

### Post by pkeeney on 2012-01-28
Thanks Ill give both a try.

---

### Post by pkeeney on 2012-01-29
> **cryptotheslow said:**
> Yes it should be possible. Who owns the files in /var/www ?
Root own /var/www and all files within

---

### Post by pkeeney on 2012-01-29
> **Lars Noodén said:**
> Let's take a few steps back.  You write that you have SSH up and running.  That means that you already have SFTP available and that can do **chmod** as one of its built-in functions.  Also, unlike [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/), it is [secure](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  

If you want to lock it down so that SFTP is allowed but shell access is not, then you can use the [ForceCommand](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) directive in [font=Courier New]sshd_config[/font].  The following locks members of the group 'webmasters' into only SFTP:

```

Subsystem sftp internal-sftp

Match Group webmasters
        ForceCommand internal-sftp

```

Then set the permissions for [font=Courier New]/var/www[/font] so that the group 'webmasters' can write to it:

```

# create group
sudo addgroup webmasters

# add a user to the group
sudo gpasswd --add pkeeney  webmasters


# set directory permissions
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

This is the error im getting when trying to chmod using sftp using filezilla

Set permissions of '/var/www/license.txt' to '677'
Command:	chmod 677 "license.txt"
Error:	set attrs for /var/www/license.txt: permission denied

I don't think the SMF forum is able to use the sftp its having trouble connecting.

---

### Post by Lars Noodén on 2012-01-29
SMF is a webforum and should not have anything to do with SFTP, though you can upload files to be used by SMF using SFTP. 

About the permissions, you have to be owner of the files to change the permissions.  There's not really a way around it that I know of.

---

### Post by cryptotheslow on 2012-01-29
> **pkeeney said:**
> Root own /var/www and all files within

And therein lies your problem. ftpuser cannot action a chmod on files owned by another user.

```
sudo chown -R ftpuser:ftpuser  /var/www
```... substitute "ftpuser" for whatever username you are using of course.

That would change the ownership of the entire directory and contents.

** However - I'm not sure if that might break other functionality that needs to write into that directory. Proceed with caution :)

---

### Post by pkeeney on 2012-01-29
> 

**** LAST EDIT I PROMISE :) **** I just chown'd a file to a different user on the ftp server and tried chmod'ing it over ftp and replicated your "-Operation not permitted" message. So I'm sticking with my original thought - it's file permissions preventing the chmod. You (as in the ftpuser) needs to own the file (or have elevated privilege) to be able to chmod it.

 Do you know how to give userftp root privilege to the www folder?

oops didn't see your above post till after i add this new one

---

### Post by cryptotheslow on 2012-01-29
I really don't think giving an ftp user admin privileges is a very good idea, even if they are confined by way of having no shell.

Just sort out the ownership / permissions of /var/www and away you go. Well that is on the assumption that this is a simple single user web server setup and only ftpuser will need to up and download there.

---

### Post by pkeeney on 2012-01-29
This is driving me nuts!
No mater what i do and how much i read i cant give userftp chmod rights. I might have to start from scratch what i probably did was install Apache as root using webmin and not with ssh using sudo. I don't know if that would make a differences or not.

---

### Post by Lars Noodén on 2012-01-29
Besides root, only the owner of a file can change its permissions with **chmod**.  I'd echo cryptotheslow's concerns about granting rights to FTP and encourage you to consider the two links in post #6 above regarding FTP.  Specifically, my recommendation would be to uninstall ProFTP completely and figure out the workflow using less complex, secure tools like SFTP.  

Is it SMF the program that needs write access or is it needed by someone who will be uploading program or data files for SMF?

---

### Post by pkeeney on 2012-01-29
Ok i got sftp working and chmod through filezilla.
Ok back to the SMF forum for some reason the built in ftp cant connect to the server. I used localhost, sftp://web-address.org and web-address.org.

Do i need to go the SMF for help or do you think its something I can do in Apache/php? Dose Apache and php know what to do with sftp out of the box?


Thanks for your help.

I'm no longer using proftp removed it out of my friends system.

---

### Post by pkeeney on 2012-01-29
Ok this is what I got.
Do i need to have sftp in there some where? 

Registered Stream Socket Transports => tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
openssl
OpenSSL support => enabled
OpenSSL Library Version => OpenSSL 1.0.0e 6 Sep 2011
OpenSSL Header Version => OpenSSL 1.0.0e 6 Sep 2011
Native OpenSSL support => enabled

---

### Post by Lars Noodén on 2012-01-30
> **pkeeney said:**
> .. for some reason the built in ftp cant connect to the server. I used localhost, sftp://web-address.org ...

That should work with an SFTP client.  [FTP and SFTP are different](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SSH_File_Transfer_Protocol_.28SFTP.29) protocols, the former is insecure.  Try the built in SFTP client instead.  It is called [sftp](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sftp.1.html)  You can also use Nautilus or Dolphin.

---

### Post by pkeeney on 2012-01-30
Sftp working fine using Filezilla but what im trying to do is use php to connect to the ssh server and use the sftp functions. 
Apparently im not the only one on the net looking for a way to use sftp with a php ftp client. 
Smf is a forum im setting up for my friend and he is not good with computers....... mental block or 
something so im trying to let Smf handle all the chmoding/permissions on the files. 
Smf has its own built in ftp client to handle this but it doesn't work with sftp.

Thanks for your help with the sftp works Great!!

Now i need help with the php side. I search the net high and low for a solution ( using php to connect to a sftp/ssl server), 
I found different thing on the subject but cant make any scene out of it. 
Ive read on some sites php5 cant handle sftp yet and others that say in can. 
Im thinking the ones that are saying php5 can is getting sftp confused with ftps.

---

### Post by Lars Noodén on 2012-01-30
Excellent.  I'm glad it works.

About PHP, hopefully they're using libraries like [libssh2](http://www.libssh2.org/) and not trying to re-invent the wheel.  

What is it that you are trying to set up for your friend that FileZilla or Nautilus cannot do?  If you use [Kate](http://kate-editor.org/) you can edit files via SFTP by providing an *sftp://user@host/path/to/some/file* URL.

---

### Post by cryptotheslow on 2012-01-30
Lars Nooden - it is the SMF forum software that requires to use FTP. In effect it FTPs back into the same machine it is on, in order to be able to chmod.

For example, you want to allow a user to upload an image - rather than permanently have a world writeable directory available - SMF dynamically FTPs in, sets a directory writeable - user upload of file occurs - SMF FTPs in again and removes the write permission.

It sounds like a fairly kludgy way to do things - but as Apache (or whatever webserver) will be running as nobody or www-data or whoever then I guess it is one way to reliably (or not!) get around any permissions problems for SMF.

---

### Post by pkeeney on 2012-01-30
> **Lars Noodén said:**
> 
What is it that you are trying to set up for your friend that FileZilla or Nautilus cannot do?

Im trying to make it as user friendly as possible. For me using Filezill or any others its no big deal but for my friend it is. To sum thing up i want to set it up so that SMF can control the file permissions in it own directory to do this it need to use ftp.

The SMF built in ftp client control's all file within it own directory (/var/www) to do this it need to connect to the ftp server
in my case sftp-server. When doing the sftp://localhost or sftp://domain.com it reports back it cant connect to server.

So to some how make it work i need to let the ftp client in SMF know what to do with the sftp on friends server by editing the php code that make up the ftp client in SMF.


If you can help me out with this one you will make about 50 people happy in the SMF community.

---

