---
title: "Amavis won't start while booting"
date: 2011-09-07
forum: General Help
---

### Post by Beejay71 on 2011-09-07
Hello all,
I am currently tracking an error in my spamassassin installation on a postfix Mailserver and I noticed that amavisd-new is not starting during booting - but can be started manually (getting the system to work just fine!)


This is how amavis is started in /ect/init.d/
-rwxr-xr-x   1 root root  3533 2010-03-29 13:38 amavis


I found the following entry in my /var/log/syslog (I replaced my real domain with "mydomain")

> Sep  5 21:55:51 mydomain amavis[872]: starting.  /usr/sbin/amavisd-new at  amavisd-new-2.6.4 (20090625), Unicode aware
Sep  5 21:55:51 mydomain amavis[872]: Perl version               5.010001and nothing more...

Once I start amavis manually with sudo the following is entered in the log file:
> Sep  5 21:38:58 mydomain amavis[2374]: starting.  /usr/sbin/amavisd-new at mydomain.com amavisd-new-2.6.4 (20090625), Unicode aware, LANG="en_US.UTF-8"
Sep  5 21:38:58 mydomain amavis[2374]: Perl version               5.010001
Sep  5 21:38:59 mydomain amavis[2381]: Net::Server: Group Not Defined.  Defaulting to EGID '127 127'
Sep  5 21:38:59 mydomain amavis[2381]: Net::Server: User Not Defined.  Defaulting to EUID '121'
Sep  5 21:38:59 mydomain amavis[2381]: Module Amavis::Conf        2.207
Sep  5 21:38:59 mydomain amavis[2381]: Module Archive::Zip        1.30
Sep  5 21:38:59 mydomain amavis[2381]: Module BerkeleyDB          0.39
Sep  5 21:38:59 mydomain amavis[2381]: Module Compress::Zlib      2.02
Sep  5 21:38:59 mydomain amavis[2381]: Module Convert::TNEF       0.17
Sep  5 21:38:59 mydomain amavis[2381]: Module Convert::UUlib      1.12
Sep  5 21:38:59 mydomain amavis[2381]: Module Crypt::OpenSSL::RSA 0.25
Sep  5 21:38:59 mydomain amavis[2381]: Module DBD::mysql          4.012...
...I noticed that "mydomain.com" is missing in the log when started while booting - probably because an configuration file cannot be accessed during booting but can be accessed while starting manually - does that mean that some permissions need to be adjusted? 



The permissions in the folder /etc/amavis/conf.d/ are set like this: -rw-r--r-- 1 root root   390 2011-09-02 12:40 50-user


I hope I am on the right track and would appreciate any comments / help from your side!

I am running Ubuntu 10.04 

Thanks in advance!

Beejay71

---

