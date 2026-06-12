---
title: "Unmet Dependencies"
date: 2012-05-25
forum: General Help
---

### Post by ashhab2010 on 2012-05-25
Why do we get unmet dependencies error?

---

### Post by 2F4U on 2012-05-25
Because the software installer is unable to find the dependency in any of the current repositories. Can you provide the exact error?

---

### Post by josephmills on 2012-05-25
open terminal and put in 
```
 apt-cache show mysql-server-5.5 
```

there are two or more **stanzas ** <er spelling 
they look like this 
```
Package: mysql-server-5.5
Priority: optional
Section: database
Installed-Size: 31872
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian MySQL Maintainers <pkg-mysql-maint@lists.alioth.debian.org>
Architecture: amd64
Source: mysql-5.5
Version: 5.5.22-0ubuntu1
Replaces: libmysqlclient-dev (<< 5.5.17~), mysql-server (<< 5.5.22-0ubuntu1), mysql-server-4.1, mysql-server-5.0, mysql-server-5.1
Provides: virtual-mysql-server
Depends: mysql-client-5.5 (>= 5.5.22-0ubuntu1), libdbi-perl, perl (>= 5.6), libc6 (>= 2.14), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, upstart-job, psmisc, passwd, lsb-base (>= 3.0-10), mysql-server-core-5.5 (= 5.5.22-0ubuntu1), upstart (>= 0.6.7-2)
Pre-Depends: mysql-common (>= 5.5.22-0ubuntu1), adduser (>= 3.40), debconf
Recommends: libhtml-template-perl
Suggests: tinyca, mailx
Breaks: libmysqlclient-dev (<< 5.5.17~), mysql-server (<< 5.5.22-0ubuntu1), mysql-server-4.1, mysql-server-5.1
Filename: pool/main/m/mysql-5.5/mysql-server-5.5_5.5.22-0ubuntu1_amd64.deb
Size: 8816482
MD5sum: d292efc961786f59eb210be659fba6a3
SHA1: 2e73dacd86c3f3a83c3903eeeb6269b13aaa3fd4
SHA256: 40f78431e2251af95ebdbca3db019d81f2cfd108d1ca2e6f8ace89fda9e3be21
Description-en: MySQL database server binaries and system database setup
 MySQL is a fast, stable and true multi-user, multi-threaded SQL database
 server. SQL (Structured Query Language) is the most popular database query
 language in the world. The main goals of MySQL are speed, robustness and
 ease of use.
 .
 This package contains all the infrastructure needed to setup system
 databases.
Homepage: http://dev.mysql.com/
Description-md5: 3ae11e16f793b3ee84f73a5fa268ad9b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: lamp-server, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master


```


notice the parts 
**Depends:**
**Pre-Depends:**
**Breaks:**


Depends mean that the package (mysql server 5.5 ) Depends on all them other programs too install 

Pre-Depends that packages must be installed before that package (mysql server 5.5) can even try to install 

Breaks Well this one kinda tells the story on its own. 

So say that I had mysql server 5.5 installed and I wanted to install mysql-server-5.1 I would get a error saying that I have unmet dependency and that it can not be installed 

there are work around's 1st you can try 
[SIZE="3"][COLOR="Red"]READ WARNING [/COLOR]
[/SIZE]```
apt-get -f install 
```
but I warn you that this can also remove things and sometimes even break things its-self 

Then there is downloading the source and fixing the error your self and rebuild the package and push to ubuntu developers. 

There are other work around's also 
 
[SIZE="3"]BUT[/SIZE]

It is best not to mess with any of that if there is a certain package that you would like to install but can not maybe post that package here and also the commands that I listed above. thanks and I hope that this helps.

---

### Post by ashhab2010 on 2012-05-25
Thanks for providing info.
I sometimes had these errors but they got solved themself, i didnt need to do anything (i might be lucky!!!!) . This was actually supposed to be a general question wherein i wanted to know what to do in case i get the error and it does not solve itself.

---

### Post by josephmills on 2012-05-25
> **ashhab2010 said:**
> Thanks for providing info.
I sometimes had these errors but they got solved themself, i didnt need to do anything (i might be lucky!!!!) . This was actually supposed to be a general question wherein i wanted to know what to do in case i get the error and it does not solve itself.

Yeah anytime that I a get a unmet dependency I open the package and fix what ever is making it not work. most the time it is for  [COLOR="DarkRed"]security[/COLOR] Reasons  and that is not good. so fixing the package or "upstream" code can have great rewards Not only for you but the others that would like to use it. 

If you feel that you 'skill' level is not there yet. For something like re-packaging. Then you should file a bug ```
ubuntu-bug <name of package>
```
and look at the Maintainers and [SIZE="3"]kindly[/SIZE] ask them if they can help you. Most are nice people and want to help. but if that is not the case all you can do is wait and try to fix it yourself or talk someone into it. There is a team in Ubuntu called M.O.T.U which stands for  "masters of the universe" These Awesome people are the ones that package up alot stuff. 

Hope this helps

---

### Post by ashhab2010 on 2012-05-25
thanks!!! is there anything else i need to keep in mind.?

---

### Post by cortman on 2012-05-25
Yes- to fix it an unmet dependencies error, usually all it takes is

```
sudo apt-get -f install
```

---

### Post by ashhab2010 on 2012-05-26
Ok, Thanks.

---

