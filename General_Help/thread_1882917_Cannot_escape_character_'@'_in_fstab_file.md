---
title: "Cannot escape character '@' in fstab file"
date: 2011-11-18
forum: General Help
---

### Post by torentas on 2011-11-18
I want to attach remote FTP directory as a local directory in my system. I will use curlftpfs line in the fstab file , but to login I have to pass my user name and password. The user name has a special character (@) and it needs to be escaped via octal ascii code. The octal ascii for '@' is 100. But when I try to enter the following into the FSTAB file, 
```
    curlftpfs#myself\100myself.com:ftpPassword@ftp://ftp.mysite.com /mnt/somedir 
```I get an error saying
>     Error connecting to ftp: Couldn't resolve host 'myself.com:ftpPassword@ftp://ftp.mysite.com'The fstab does not recognize escaped symbol @ (\100) and thinks that the FTP site should start immediately after the @ symbol (just like I haven't escaped it). 


Can someone help? Why I cannot escape @, when it can be done for space character, for example?

---

### Post by Jacobonbuntu on 2011-11-18
It may not be much of a help, but I believe it is because "@" has a specific function manytimes as a trigger. I know spaces can be escaped, but the way in which is not quite universal in different “system areas”; in fstab with \043, in my automatic backups by putting the names with spaces between “”. anyway the @ -symbol has to be disarmed as a trigger, maybe you ca experiment with “” ?

---

### Post by matt_symes on 2011-11-18
Hi

I have never used curlftp so this may be way off.
[FONT=monospace]
[/FONT]> curlftpfs#myself\100myself.com:ftpPassword@ftp://ftp.mysite.com /mnt/somedirAre you sure this is correct ? 

[http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html](http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html)

This seems to suggest you may need to do

```
curlftpfs#ftpmyself:ftpPassword@ftp://ftp.mysite.com /mnt/somedir
```Where myself is the user name, Password is the password and ftp.mysite.com is the url to the ftp server.

On that web site it says. Notice it also sets up permissions.

```
curlftpfs#ftpUsername:ftpPassword@ftp://ftpUrl /localDirectory fuse  rw,uid=1000,umask=0777,user,suid,allow_other,exec,auto,utf8  0   1
```The article is dated in August 2010.

Kind regards

---

