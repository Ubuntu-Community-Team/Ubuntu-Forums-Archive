---
title: "running cgi scripts in browser"
date: 2010-12-08
forum: General Help
---

### Post by prabhanjan2906 on 2010-12-08
I have installed apache2. i am not able to execute the perl script in the browser. i restarted the apache2 and found the following in the error log.
Options ExecCGI is off in this directory: /var/www/cgi-bin/trypost.cgi
File does not exist: /var/www/favicon.ico

i added the following lines in /etc/apache2/apache2.conf

<Directory "/var/www/cgi-bin/">
    Options FollowSymLinks ExecCGI Indexes 
    AllowOverride All
</Directory>

then this error 
Options ExecCGI is off in this directory: /var/www/cgi-bin/trypost.cgi
vanished. but i get File does not exist: /var/www/favicon.ico error. what should i do to execute the programs on the browser? 

Thanks in advance

---

### Post by daqron on 2010-12-17
The favicon error is [not fatal]("http://www.tfug.org/pipermail/tfug_tfug.org/2005-February/008418.html"). It's just Apache telling you there is no favicon. You could add one, or ignore the error. Either way, it's not impacting your ability to execute CGI scripts.

What does the browser say when you try to access the script? Is it 500 forbidden? Internal server error?

Is the script world-executable (chmod 755 script.cgi)? Do you have fatals and warnings on to help diagnose problems?
```
use CGI;
use CGI::Carp qw(warningsToBrowser fatalsToBrowser);
```
I think the favicon error is distracting you from whatever is really going on.

---

