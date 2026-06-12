---
title: "Using apache to execute a perl program that kills a process"
date: 2009-08-17
forum: General Help
---

### Post by holandes777 on 2009-08-17
I'm building a console for launching and stopping programs. There is a launcher.pl and a launcher script plus a halt.pl in /usr/lib/cgi-bin. All these work if executed as a common user.
 
When the scripts or perl programs are executed via a browser, they do execute, but they don't do what is needed. I have a similar setup in Fedora Core 8 and these programs work via web browsers. I am sure it is a security issue but am unfamiliar with ubuntu's security (which is why I ask your help).
 
/var/log/apache2/error.log for the "halt.pl" program states the following:
 
[Mon Aug 17 04:39:27 2009] [error] [client 111.222.111.222] kill: Operation not permitted, referer: [http://222.111.222.111/cgi-bin/halt.pl](http://222.111.222.111/cgi-bin/halt.pl)
 
for the launcher.pl's error log states:
 
[Mon Aug 17 04:38:27 2009] [error] [client 111.222.111.222] Can't open perl script "abc.pl": Permission denied, referer: [http://222.111.222.111/cgi-bin/launcher.pl](http://222.111.222.111/cgi-bin/launcher.pl)
 
So they both execute their content, but are prevented from starting or stopping other processes.
 
Your assistance is appreciated

---

### Post by holandes777 on 2009-08-17
I made progress: I had symbolic links from /usr/lib/cgi-bin to the perl programs in the users home directory.
 
When I reversed this (actually putting all the programs in /usr/lib/cgi-bin) the content executed. 
 
So the sloution was to put the perl programs in teh /usr/lib/cgi-bin directory and give the user access by creating a link in the user's home directory that points to the file. This allows the user to edit his program and allows apache to execute it.

---

