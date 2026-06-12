---
title: "Installing OpenERP"
date: 2009-12-13
forum: General Help
---

### Post by Yumi on 2009-12-13
OpenERP Server and Client are in the Karmic Repositories. Automatically Postgresql is also intalled. But opening the client after intall fails to connect to the OpenERP server.

There are a number of howto's around but all for 8.04 or 9.04 non for 9.10. 

Apparently OpenERP still requires python-xml which is not in the repositories any more!

Anybody has a good intallation guide for Karmic?

Michael

---

### Post by Yumi on 2009-12-13
Reading through a number of posts it seems unlikely that OpenERP will work on Ubuntu 9.10. If at all, it will require lots of work. One major stumbling block is the requirement of python-xml which is no longer available for Ubuntu. 

Leaves the change of Distribution as a solution. If anybody has a suggestion to as to which one works well with OpenERP please post.

Michael

---

### Post by coolmanlg on 2009-12-14
Am having the same problem with Openerp on Karmic. Any solution yet?

---

### Post by Yumi on 2009-12-14
I got in the OpenERP forum the following reply:
*>  check this post [http://www.openobject.com/forum/post46084.html](http://www.openobject.com/forum/post46084.html)*

The link provides the python-xml which is missing. But then I tried to install 5.0.6 from OpenERP's website. Server installed, but Client failed. It is all a big mess. My guess is that in Karmic the directories have changed. I post here if I get a further reply in the other forum.

Michael

---

### Post by Agent20 on 2009-12-15
I installed the from the Karmic Repositories and then followed the extra instructions given on this page:

[http://doc.openerp.com/book/1/1_1_Inst_Config/1_1_Inst_Config_install.html](http://doc.openerp.com/book/1/1_1_Inst_Config/1_1_Inst_Config_install.html)

(You have to scroll down to get to the Linux instructions)

I did not install python-xml, but I can still use the client OK for the options that I have tried so far.

---

### Post by Yumi on 2009-12-15
Thank you Agent20. Following your advice and the steps in the OpenERP book worked for me too. I am connected to the server, created a database and am busy learning the system.

Michael

---

### Post by alecwk on 2009-12-26
> **Agent20 said:**
> I installed the from the Karmic Repositories and then followed the extra instructions given on this page:

[http://doc.openerp.com/book/1/1_1_Inst_Config/1_1_Inst_Config_install.html](http://doc.openerp.com/book/1/1_1_Inst_Config/1_1_Inst_Config_install.html)

(You have to scroll down to get to the Linux instructions)

I did not install python-xml, but I can still use the client OK for the options that I have tried so far.

I try that as well and everything seems to be working on Karmic except, when I want to backup and restore a database. When I backup a database, the file has 0 byte. Restore successful, but cannot login.  Are you facing the same problem?

---

### Post by aaronchall on 2010-02-04
Any further luck?  Figure this out?

---

### Post by aaronchall on 2010-02-05
I have 9.10, and here's what I've done so far, and I'm not sure it's working:

Installed the OpenERP client from Ubuntu Software Center
Opened it and tried to run it, it wouldn't let me set up a database...
After much searching for a solution, I got a link to this page, [http://doc.openerp.com/install/linux/server/index.html#example-on-ubuntu](http://doc.openerp.com/install/linux/server/index.html#example-on-ubuntu), where a message there told me to do the following:

Open a terminal and

:~$ sudo apt-get openerp-server
E: Invalid operation openerp-server (oh geez...)

~$ sudo apt-get install openerp-server
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libuser-perl gdesklets-data python-numeric libcarp-clan-perl python-soappy
  libwww-search-perl libfile-slurp-perl python-fpconst libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  graphviz postgresql postgresql-8.4 postgresql-client-8.4
  postgresql-client-common postgresql-common python-libxslt1 python-lxml
  python-psycopg2 python-pychart python-pydot
Suggested packages:
  graphviz-doc oidentd ident-server postgresql-doc-8.4 python-libxslt1-dbg
  python-lxml-dbg python-pychart-doc
Recommended packages:
  postgresql-client
The following NEW packages will be installed:
  graphviz openerp-server postgresql postgresql-8.4 postgresql-client-8.4
  postgresql-client-common postgresql-common python-libxslt1 python-lxml
  python-psycopg2 python-pychart python-pydot
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.4MB of archives.
After this operation, 104MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/main graphviz 2.20.2-3ubuntu5 [424kB]
Get:2 http://us.archive.ubuntu.com karmic/main python-libxslt1 1.1.24-2ubuntu2 [157kB]
Get:3 http://us.archive.ubuntu.com karmic/main python-lxml 2.1.5-1ubuntu2 [1,013kB]
Get:4 http://us.archive.ubuntu.com karmic/universe python-psycopg2 2.0.8-0ubuntu2 [170kB]
Get:5 http://us.archive.ubuntu.com karmic/universe python-pydot 1.0.2-1 [19.4kB]
Get:6 http://us.archive.ubuntu.com karmic/universe python-pychart 1.39-7 [81.8kB]
Get:7 http://us.archive.ubuntu.com karmic/universe openerp-server 5.0.5-1 [8,671kB]
Get:8 http://us.archive.ubuntu.com karmic/main postgresql-client-common 101 [49.8kB]
Get:9 http://us.archive.ubuntu.com karmic-updates/main postgresql-client-8.4 8.4.2-0ubuntu9.10 [787kB]
Get:10 http://us.archive.ubuntu.com karmic/main postgresql-common 101 [85.6kB] 
Get:11 http://us.archive.ubuntu.com karmic-updates/main postgresql-8.4 8.4.2-0ubuntu9.10 [3,893kB]
Get:12 http://us.archive.ubuntu.com karmic-updates/main postgresql 8.4.2-0ubuntu9.10 [10.2kB]
Fetched 15.4MB in 3min 22s (76.0kB/s)                                          
Preconfiguring packages ...
Selecting previously deselected package graphviz.
(Reading database ... 228712 files and directories currently installed.)
Unpacking graphviz (from .../graphviz_2.20.2-3ubuntu5_i386.deb) ...
Selecting previously deselected package python-libxslt1.
Unpacking python-libxslt1 (from .../python-libxslt1_1.1.24-2ubuntu2_i386.deb) ...
Selecting previously deselected package python-lxml.
Unpacking python-lxml (from .../python-lxml_2.1.5-1ubuntu2_i386.deb) ...
Selecting previously deselected package python-psycopg2.
Unpacking python-psycopg2 (from .../python-psycopg2_2.0.8-0ubuntu2_i386.deb) ...
Selecting previously deselected package python-pydot.
Unpacking python-pydot (from .../python-pydot_1.0.2-1_all.deb) ...
Selecting previously deselected package python-pychart.
Unpacking python-pychart (from .../python-pychart_1.39-7_all.deb) ...
Selecting previously deselected package openerp-server.
Unpacking openerp-server (from .../openerp-server_5.0.5-1_all.deb) ...
Selecting previously deselected package postgresql-client-common.
Unpacking postgresql-client-common (from .../postgresql-client-common_101_all.deb) ...
Selecting previously deselected package postgresql-client-8.4.
Unpacking postgresql-client-8.4 (from .../postgresql-client-8.4_8.4.2-0ubuntu9.10_i386.deb) ...
Selecting previously deselected package postgresql-common.
Unpacking postgresql-common (from .../postgresql-common_101_all.deb) ...
Selecting previously deselected package postgresql-8.4.
Unpacking postgresql-8.4 (from .../postgresql-8.4_8.4.2-0ubuntu9.10_i386.deb) ...
Selecting previously deselected package postgresql.
Unpacking postgresql (from .../postgresql_8.4.2-0ubuntu9.10_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up graphviz (2.20.2-3ubuntu5) ...

Setting up python-libxslt1 (1.1.24-2ubuntu2) ...

Setting up python-lxml (2.1.5-1ubuntu2) ...

Setting up python-psycopg2 (2.0.8-0ubuntu2) ...

Setting up python-pydot (1.0.2-1) ...

Setting up python-pychart (1.39-7) ...

Setting up openerp-server (5.0.5-1) ...

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Open ERP uses a PostgreSQL database to store its data. With the first *
* generation of packages, you have to setup this database manually.     *
* Please read /usr/share/doc/openerp-server/README.Debian how to do it. *
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *

Starting openerp-server: openerp-server.

Setting up postgresql-client-common (101) ...
Setting up postgresql-client-8.4 (8.4.2-0ubuntu9.10) ...
update-alternatives: using /usr/share/postgresql/8.4/man/man1/psql.1.gz to provide /usr/share/man/man1/psql.1.gz (psql.1.gz) in auto mode.

Setting up postgresql-common (101) ...
Adding user postgres to group ssl-cert
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
  en_au
  en_gb
  en_us
  en_za

Setting up postgresql-8.4 (8.4.2-0ubuntu9.10) ...
Creating new cluster (configuration: /etc/postgresql/8.4/main, data: /var/lib/postgresql/8.4/main)...
Moving configuration file /var/lib/postgresql/8.4/main/postgresql.conf to /etc/postgresql/8.4/main...
Moving configuration file /var/lib/postgresql/8.4/main/pg_hba.conf to /etc/postgresql/8.4/main...
Moving configuration file /var/lib/postgresql/8.4/main/pg_ident.conf to /etc/postgresql/8.4/main...
Configuring postgresql.conf to use port 5432...
update-alternatives: using /usr/share/postgresql/8.4/man/man1/postmaster.1.gz to provide /usr/share/man/man1/postmaster.1.gz (postmaster.1.gz) in auto mode.
 * Starting PostgreSQL 8.4 database server                               [ OK ] 

Setting up postgresql (8.4.2-0ubuntu9.10) ...
Processing triggers for python-support ...
```THEN
$ openerp-server
```
[2010-02-04 22:55:31,806] INFO:server:version - 5.0.5
[2010-02-04 22:55:31,807] INFO:server:addons_path - /usr/lib/openerp-server/addons
[2010-02-04 22:55:31,807] INFO:server:database hostname - localhost
[2010-02-04 22:55:31,807] INFO:server:database port - 5432
[2010-02-04 22:55:31,807] INFO:server:database user - aaron
[2010-02-04 22:55:31,807] INFO:objects:initialising distributed objects services
sh: bzr: not found
No LSB modules are available.
[2010-02-04 22:55:32,455] CRITICAL:xml-rpc:[01]: 
[2010-02-04 22:55:32,455] CRITICAL:xml-rpc:[02]: Environment Information : 
[2010-02-04 22:55:32,455] CRITICAL:xml-rpc:[03]: System : Linux-2.6.31-17-generic-i686-with-Ubuntu-9.10-karmic
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[04]: OS Name : posix
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[05]: Distributor ID:    Ubuntu
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[06]: Description:    Ubuntu 9.10
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[07]: Release:    9.10
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[08]: Codename:    karmic
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[09]: Operating System Release : 2.6.31-17-generic
[2010-02-04 22:55:32,456] CRITICAL:xml-rpc:[10]: Operating System Version : #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009
[2010-02-04 22:55:32,457] CRITICAL:xml-rpc:[11]: Operating System Architecture : 32bit
[2010-02-04 22:55:32,457] CRITICAL:xml-rpc:[12]: Operating System Locale : en_US.UTF8
[2010-02-04 22:55:32,457] CRITICAL:xml-rpc:[13]: Python Version : 2.6.4
[2010-02-04 22:55:32,457] CRITICAL:xml-rpc:[14]: OpenERP-Server Version : 5.0.5
[2010-02-04 22:55:32,457] CRITICAL:xml-rpc:[15]: Last revision No. & ID : 
[2010-02-04 22:55:32,457] CRITICAL:xml-rpc:[16]: Error occur when starting the server daemon: [Errno 98] Address already in use
```

and "CRITICAL" was in red.

I'm guessing this may be due to the missing xml python package that 9.10 lacks?  Or perhaps I just know nothing, being a total noob to linux and ignorant of programming.

But I need a CRM package, and I figured it would be a good idea, if I needed to learn how to use one, and I wanted it to be a Linux OSS, to learn an industrial strength program with ERP too.  (I am finishing my MBA, and being able to speak intelligently of CRM and ERP usage and not just implementation may be a plus.)

---

### Post by erolerten on 2010-03-05
how can I uninstall the packages I had installed from the source?

any ideas?

I am thinking of reinstalling the whole system (was experimenting with my secondary computer)

---

### Post by erolerten on 2010-03-09
I have also installed it from synaptic
followed the instructions in the openerp book

and received the same error message:
no LSB modules available

---

### Post by Fintan on 2010-04-05
Foe 9.10 I found this:
[http://opensourceconsulting.wordpress.com/2009/09/15/openerp-all-in-one-installer-update-for-dummies/]("http://opensourceconsulting.wordpress.com/2009/09/15/openerp-all-in-one-installer-update-for-dummies/")

It works fine if you follow the instructions closely.

Also if you don't want to use the default IP settings and are on a dhcp line then you will have to generate an IP with something like [no-ip]("http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html") and edit your /etc/host accordingly before installation.

I hope these issues get resolved in lucid as there is no reason why openerp should be in the repos if it is not usable.
I believe that as of version 5.04 openerp does not depend on Python-xml any more but don't quote me on that;)

Anyway I hope this helps :)

---

### Post by erolerten on 2010-04-20
after long search I came across this link:
[http://hubpages.com/hub/lling-OpenERP-on-Ubuntu-910]("http://hubpages.com/hub/lling-OpenERP-on-Ubuntu-910")

i have done all the instructions and have right now a working erp system...

---

