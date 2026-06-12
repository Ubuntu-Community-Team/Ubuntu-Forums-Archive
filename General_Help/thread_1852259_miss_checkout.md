---
title: "miss checkout??"
date: 2011-09-29
forum: General Help
---

### Post by ngubk on 2011-09-29
hi all!
 help me.. 
giang@giang-laptop:~$ cd /opt/OpenIMSCore/ser_ims
\giang@giang-laptop:/opt/OpenIMSCore/ser_ims$ sudo svn checkout [http://svn.berlis.de/svnroot/repos/openimscore/ser_ims/trunk](http://svn.berlis.de/svnroot/repos/openimscore/ser_ims/trunk) ser_ims
[sudo] password for giang: 
sudo: svn: command not found
giang@giang-laptop:/opt/OpenIMSCore/ser_ims$ 
  I'm starting to learning linux. :(thanks

---

### Post by oldos2er on 2011-09-29
You need to install subversion ```
sudo apt-get update && sudo apt-get install subversion
```

---

### Post by ngubk on 2011-09-30
thanks hihi
I'll try it.:P

---

### Post by ngubk on 2011-09-30
> **oldos2er said:**
> You need to install subversion ```
sudo apt-get update && sudo apt-get install subversion
```


[SIZE=4][COLOR=Red] hi oldos2er. I did so, but I don't know. i have to do what :(. [/COLOR][/SIZE]. I 
giang@giang-laptop:~$ sudo apt-get update && sudo apt-get install subversion
[sudo] password for giang: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [516kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]     
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [229kB]        
Fetched 804kB in 16s (47.3kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-kb-dev ttf-dejavu-extra java-common
  libxdmcp-dev xtrans-dev x11proto-core-dev libjaxp1.3-java libxt-dev
  tzdata-java libxerces2-java x11proto-input-dev libpthread-stubs0-dev
  libxau-dev libpthread-stubs0 libx11-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libapr1 libaprutil1 libsvn1
Suggested packages:
  subversion-tools db4.8-util
The following NEW packages will be installed:
  libapr1 libaprutil1 libsvn1 subversion
0 upgraded, 4 newly installed, 0 to remove and 10 not upgraded.
Need to get 1,412kB of archives.
After this operation, 6,836kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libapr1 1.3.8-1ubuntu0.3 [117kB]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libaprutil1 1.3.9+dfsg-3ubuntu0.10.04.1 [85.6kB]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libsvn1 1.6.6dfsg-2ubuntu1.3 [840kB]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main subversion 1.6.6dfsg-2ubuntu1.3 [370kB]
Fetched 1,412kB in 59s (23.7kB/s)                                              
Selecting previously deselected package libapr1.
(Reading database ... 130435 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.3.8-1ubuntu0.3_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.6dfsg-2ubuntu1.3_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.6.6dfsg-2ubuntu1.3_i386.deb) ...
Processing triggers for man-db ...
Setting up libapr1 (1.3.8-1ubuntu0.3) ...

Setting up libaprutil1 (1.3.9+dfsg-3ubuntu0.10.04.1) ...

Setting up libsvn1 (1.6.6dfsg-2ubuntu1.3) ...

Setting up subversion (1.6.6dfsg-2ubuntu1.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
giang@giang-laptop:~$ cd /opt/OpenIMSCore/ser_ims
giang@giang-laptop:/opt/OpenIMSCore/ser_ims$ sudo svn checkout [http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk](http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk) ser_ims
A    ser_ims/stats.c
A    ser_ims/modparam.c
A    ser_ims/qvalue.h
A    ser_ims/ip_addr.c
A    ser_ims/stats.h
A    ser_ims/AUTHORS
A    ser_ims/modparam.h
A    ser_ims/cfg.lex
A    ser_ims/scripts
A    ser_ims/scripts/filter_log.sh
A    ser_ims/scripts/em_serv_update
A    ser_ims/scripts/em_serv_update/civic_belgium.sql
A    ser_ims/scripts/em_serv_update/fokus_building_3_areas.sql
A    ser_ims/scripts/em_serv_update/select_de_em_mapping.sql
A    ser_ims/scripts/em_serv_update/civic_spain.sql
A    ser_ims/scripts/em_serv_update/update_lost_server_db.sh
A    ser_ims/scripts/em_serv_update/update_ims_core.sh
A    ser_ims/scripts/em_serv_update/civic_germany.sql
A    ser_ims/scripts/em_serv_update/update_hss_db.sh
A    ser_ims/scripts/em_serv_update/berlin_mitte_geodetic.sql
A    ser_ims/scripts/harv_ser.sh
A    ser_ims/scripts/mysql
A    ser_ims/scripts/mysql/my_create.sql
A    ser_ims/scripts/mysql/my_drop.sql
A    ser_ims/scripts/mysql/ser_mysql.sh
A    ser_ims/scripts/mysql/my_data.sql
A    ser_ims/scripts/oracle
A    ser_ims/scripts/oracle/or_create.sql
A    ser_ims/scripts/oracle/or_drop.sql
A    ser_ims/scripts/oracle/or_data.sql
A    ser_ims/scripts/sc
A    ser_ims/scripts/postgres
A    ser_ims/scripts/postgres/pg_create.sql
A    ser_ims/scripts/postgres/pg_drop.sql
A    ser_ims/scripts/postgres/ser_postgres.sh
A    ser_ims/scripts/postgres/pg_data.sql
A    ser_ims/scripts/sc_unixsock
A    ser_ims/scripts/serconf.sh
A    ser_ims/scripts/serstats
A    ser_ims/scripts/dbtext
A    ser_ims/scripts/dbtext/ser_dbtext.sh
A    ser_ims/scripts/dbtext/ser_db
A    ser_ims/scripts/dbtext/ser_db/presentity_contact
A    ser_ims/scripts/dbtext/ser_db/gw_grp
A    ser_ims/scripts/dbtext/ser_db/acc
A    ser_ims/scripts/dbtext/ser_db/pdt
A    ser_ims/scripts/dbtext/ser_db/grp
A    ser_ims/scripts/dbtext/ser_db/trusted
A    ser_ims/scripts/dbtext/ser_db/rls_vs_names
A    ser_ims/scripts/dbtext/ser_db/attr_types
A    ser_ims/scripts/dbtext/ser_db/uri
A    ser_ims/scripts/dbtext/ser_db/missed_calls
A    ser_ims/scripts/dbtext/ser_db/silo
A    ser_ims/scripts/dbtext/ser_db/presentity
A    ser_ims/scripts/dbtext/ser_db/location
A    ser_ims/scripts/dbtext/ser_db/contact_attrs
A    ser_ims/scripts/dbtext/ser_db/watcherinfo
A    ser_ims/scripts/dbtext/ser_db/i18n
A    ser_ims/scripts/dbtext/ser_db/presentity_persons
A    ser_ims/scripts/dbtext/ser_db/lcr
A    ser_ims/scripts/dbtext/ser_db/sd_attrs
A    ser_ims/scripts/dbtext/ser_db/domain_attrs
A    ser_ims/scripts/dbtext/ser_db/customers
A    ser_ims/scripts/dbtext/ser_db/offline_winfo
A    ser_ims/scripts/dbtext/ser_db/phonebook
A    ser_ims/scripts/dbtext/ser_db/version
A    ser_ims/scripts/dbtext/ser_db/ipmatch
A    ser_ims/scripts/dbtext/ser_db/presentity_extensions
A    ser_ims/scripts/dbtext/ser_db/domain_settings
A    ser_ims/scripts/dbtext/ser_db/speed_dial
A    ser_ims/scripts/dbtext/ser_db/user_attrs
A    ser_ims/scripts/dbtext/ser_db/credentials
A    ser_ims/scripts/dbtext/ser_db/tuple_notes
A    ser_ims/scripts/dbtext/ser_db/rls_subscription
A    ser_ims/scripts/dbtext/ser_db/domain
A    ser_ims/scripts/dbtext/ser_db/rls_vs
A    ser_ims/scripts/dbtext/ser_db/tuple_extensions
A    ser_ims/scripts/dbtext/ser_db/uri_attrs
A    ser_ims/scripts/dbtext/ser_db/global_attrs
A    ser_ims/scripts/dbtext/ser_db/gw
A    ser_ims/scripts/dbtext/ser_db/presentity_notes
A    ser_ims/scripts/dbtext/ser_db/cpl
A    ser_ims/scripts/sc_tcp
A    ser_ims/tcp_info.h
A    ser_ims/ip_addr.h
A    ser_ims/daemonize.c
A    ser_ims/action.c
A    ser_ims/tsend.c
A    ser_ims/tools
A    ser_ims/tools/pike_top
A    ser_ims/tools/pike_top/INSTALL
A    ser_ims/tools/pike_top/pike_top.c
A    ser_ims/tools/pike_top/Makefile
A    ser_ims/daemonize.h
A    ser_ims/hashes.h
A    ser_ims/tsend.h
A    ser_ims/action.h
A    ser_ims/doc
A    ser_ims/doc/tmemo
A    ser_ims/doc/tmemo/tmemo-jiri-phone-shopping.txt
A    ser_ims/doc/timers.txt
A    ser_ims/doc/serfaq
A    ser_ims/doc/serfaq/serfaq.xml
A    ser_ims/doc/serfaq/Makefile
A    ser_ims/doc/parse_headers.txt
A    ser_ims/doc/rpc
A    ser_ims/doc/rpc/rpc_example.png
A    ser_ims/doc/rpc/rpc_example.dia
A    ser_ims/doc/rpc/ser_rpc.xml
A    ser_ims/doc/rpc/Makefile
A    ser_ims/doc/cvs-commit-rules.txt
A    ser_ims/doc/seruser
A    ser_ims/doc/seruser/operation.xml
A    ser_ims/doc/seruser/apps.xml
A    ser_ims/doc/seruser/otherapps.xml
A    ser_ims/doc/seruser/db_fifo.xml
A    ser_ims/doc/seruser/seruser.xml
A    ser_ims/doc/seruser/voicemail.xml

---

### Post by nothingspecial on 2011-09-30
Hi, you need to read the README and INSTALL files contained in the director you just checked out.

First you need to install the dependencies listed in the debian section of the INSTALL file, then you need to decide how you want to compile it from the options it gives you.

---

### Post by ngubk on 2011-09-30
> **nothingspecial said:**
> Hi, you need to read the README and INSTALL files contained in the director you just checked out.

First you need  install the dependencies listed in the debian section of the INSTALL file, then you need to decide how you want to compile it from the options it gives you.

. I have to install a simulation. this is levers which i have to do
can you help me ? :). may be  any advice ?. I'm from Vietnam. thanks so much. :)
I'm at  3 lever.hi


Please follow the steps below to configure OpenIMSCore on localhost, later steps will be listed to switch between localhost and a specific IP address:

Prerequisites:

a. libxml2 (with development)
b. libmysql (with development)
c. bind9
d. bison
e. flex
f. mysql-server
g. ant
h. make
i. jdk1.5
j. gcc3/4
k. ipsec-tools


1. Go to / directory through command prompt and

mkdir opt
cd opt
mkdir OpenIMSCore
cd OpenIMSCore
mkdir ser_ims
mkdir FHoSS

2. Change the permissions for opt folder created:

chmod 777 -R /opt

3. Check out the code for OpenIMSCore

cd /opt/OpenIMSCore/

ser_ims: sudo svn checkout [http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk](http://svn.berlios.de/svnroot/repos/openimscore/ser_ims/trunk) ser_ims

FHoSS: sudo svn checkout [http://svn.berlios.de/svnroot/repos/openimscore/FHoSS/branches/07_Dynamic_Service_Activation/](http://svn.berlios.de/svnroot/repos/openimscore/FHoSS/branches/07_Dynamic_Service_Activation/)

4. Configure ser_ims

cd ser_ims
sudo make install-libs all

5. Install FHoSS

cd cd FHoSS
ant compile deploy
cd ..

6. Mysql dumps

mysql -u root -p -h localhost < ser_ims/cfg/icscf.sql
mysql -u root -p -h localhost < FHoSS/scripts/hss_db.sql  
mysql -u root -p -h localhost < FHoSS/scripts/userdata.sql

7. Copy and dump the following

cp ser_ims/cfg/*.cfg /opt/OpenIMSCore
cp ser_ims/cfg/*.xml /opt/OpenIMSCore
cp ser_ims/cfg/*.sh /opt/OpenIMSCore

8. Make following configuration changes:

8.1 Edit /etc/bind/named.conf by adding following zone in it:

zone "open-ims.test" {
type master;
file "/etc/bind/open-ims.dnszone";
};

8.2 Copy open-ims.dnszone file to /etc/bind/

sudo cp ser_ims/cfg/open-ims.dnszone etc/bind/

8.3 Edit /etc/resolv.conf

# Generated by NetworkManager
search open-ims.test
domain open-ims.test
nameserver 127.0.0.1

8.4 Edit etc/hosts

127.0.0.1 localhost
127.0.0.1 open-ims.test mobicents.open-ims.test ue.open-ims.test presence.open-ims.test icscf.open-ims.test scscf.open-ims.test
pcscf.open- ims.test hss.open-ims.test

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

8.5 Restart bind server:

sudo /etc/init.d/bind9 restart

9. Confirm your configuration changes by digging the domain:
dig open-ims.test (It must list 127.0.0.1 in your answer sections)

10. Start all nodes and hss:

10.1 cd opt/OpenIMSCore
10.2 ./pcscf.sh
10.3 ./scscf.sh
10.4 ./icsscf.sh
10.5 cd FHoSS/deploy
10.6 sh startup.sh

Thats about it.

Now switching from localhost to a specific IP edit all the undermentioned files, by replacing all 127.0.0.1 to your specific IP say for eg: 192.168.0.100:

1. edit /etc/resolv.conf

2. edit /etc/hosts

3. edit /etc/bind/open-ims.test

4. restart bind: sudo /edit/init.d/bind9 restart

5. check: dig open-ims.test

6. Change Nodes setting:

6.1 icscf.cfg & icscf.xml (opt/OpenIMSCore/)
6.2 pcscf.cfg & pcscf.xml
6.3 scscf.cfg & scscf.xml

7. Change FHoSS setting

7.1 DiameterPeerHSS.xml (FHoSS/deploy)
7.2 hss.properties (FHoSS/deploy) 

TROUBLE SHOOTING
1.Type before run startup.sh :export JAVA_HOME="/usr/lib/jvm/java-6-openjdk/jre"
2.mkdir "/usr/local/lib/ser"
  cp /usr/local/lib/ser /opt/OpenIMSCore/ser_ims/lib/cds/lib_ser_cds.so

OTHER USEFUL LINKS:
[http://vntelecom.org/diendan/showthread.php?t=731&page=2](http://vntelecom.org/diendan/showthread.php?t=731&page=2)
[http://www.openimscore.org/installation_guide](http://www.openimscore.org/installation_guide)
[http://www.webupd8.org/2009/07/how-to-close-port-in-linux.html](http://www.webupd8.org/2009/07/how-to-close-port-in-linux.html)

---

### Post by caojinyu on 2011-09-30
> **ngubk said:**
> hi all!
 help me.. 
giang@giang-laptop:~$ cd /opt/OpenIMSCore/ser_ims
\giang@giang-laptop:/opt/OpenIMSCore/ser_ims$ sudo svn checkout [http://svn.berlis.de/svnroot/repos/openimscore/ser_ims/trunk](http://svn.berlis.de/svnroot/repos/openimscore/ser_ims/trunk) ser_ims
[sudo] password for giang: 
sudo: svn: command not found
giang@giang-laptop:/opt/OpenIMSCore/ser_ims$ 
  I'm starting to learning linux. :(thanks

i think ubuntu it's very funny.my email is [email]caojinyu@msn.com[/email],i hope you will be my best friend,i ama waiting for message.let's study together .

---

