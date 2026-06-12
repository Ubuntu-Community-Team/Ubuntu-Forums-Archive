---
title: "Teamspeak 3 issue with libmysqlclient15off?"
date: 2011-11-08
forum: General Help
---

### Post by CorrupterTheLost on 2011-11-08
Greetings, its been a while since this type of issue was visited and i would like to post my latest findings on the latest crop of this problem.

So it would seem the the developers of teamspeak 3 only really had 1 version of libmysqlclient150ff in mind when they developed the mysql support for ts3.  I had a ts3 server running for a bit on ubuntu 10.04 and things we're fine till i decided i needed to update my linux box to 11.10.  So rather than upgrade the system using the commands i started from scratch and blew it all away.  From a fresh install i installed the following packages,

mysql-client and mysql-server however these no longer supply the previously needed libmysqlclient15off for the beta version of ts3 i was using before.  So, after getting the system up and seeing the mysql db running smoothly i went ahead and downloaded the latest linux 32bit variety of ts3 server which is no longer in beta.  popped it on the machine, configured my ini files with the appropriate information and setup the ts3 user that would be used to execute this whole mess.  went ahead and tried to run it for the first time to get my keys and voila, it doesnt like that there again is no libmysqlclient.so.15 so i happen to have a copy of actual package from my previous ts3 server that was running happily in beta up to this point, went ahead and dpkg -i libmysqlclient15off and its in.  Attempt number two at running the server except its still giving me the same message. So i hammer out ldd libts3db_mysql.so and this time it shows all dependencies are there and present. Hmmm as i scratch my head... What the hecks going on here?  So i methodically check all the steps i did, making sure to the best of my knowledge to determine if i had missed one or not and still nothing... not a change in the results.  

So where am i at?  i thought perhaps there was different versions of libmysqlclient.so.15 out there so i tracked down a half dozen packages for a few different distros even, started plugging them all with the same results, each time ldd libts3db_mysql.so showing the dependencies there.... I've tried all the links from the 5 or 6 so posts on this forum and the teamspeak users forum about this issue and replicated each of their attempts, even the ones that people have said worked for them.  Perhaps there is something wrong with the 32bit version of ts3 linux server and its compatability with a specific version?  I dont know, but i know this, i've tried alot and got a whole lot more of no where.  Anyone have any ideas?

I'll paste here some things about what im using as my current testbed.

OS: Linux Ubuntu 11.10 Oneiric 32bit.
TS3: Linux Server x86 3.0.0  from 4netplayers
mysql 5.1.58-1ubuntu1 (Ubuntu)
libmysqlclient15off versions tried:
libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb
libmysqlclient15off_5.0.51a-3ubuntu5.8_i386.deb
libmysqlclient15off_5.0.51a-24+lenny5_i386.deb
MySQL-shared-compat-6.0.9-0.sles9.i586.rpm (yes i know this is an rpm, i used alien to convert it to .deb)

each time it produced these results:

```
libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386

:/opt/ts3server$ ldd libts3db_mysql.so
        linux-gate.so.1 =>  (0xb773f000)
        libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15 (0xb754e000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb7463000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7438000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb741a000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb729e000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7283000)
        libcrypt.so.1 => /lib/i386-linux-gnu/libcrypt.so.1 (0xb7252000)
        libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xb7238000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb7223000)
        /lib/ld-linux.so.2 (0xb7740000)


libmysqlclient15off_5.0.51a-3ubuntu5.8_i386

:/opt/ts3server$ ldd libts3db_mysql.so
        linux-gate.so.1 =>  (0xb7802000)
        libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15 (0xb7612000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb7527000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb74fc000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb74de000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7362000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7347000)
        libcrypt.so.1 => /lib/i386-linux-gnu/libcrypt.so.1 (0xb7316000)
        libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xb72fc000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb72e7000)
        /lib/ld-linux.so.2 (0xb7803000)


libmysqlclient15off_5.0.51a-24+lenny5_i386

:/opt/ts3server$ ldd libts3db_mysql.so
        linux-gate.so.1 =>  (0xb7727000)
        libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15 (0xb752e000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb7443000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7418000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb73fa000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb727e000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7263000)
        libcrypt.so.1 => /lib/i386-linux-gnu/libcrypt.so.1 (0xb7232000)
        libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xb7218000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb7203000)
        /lib/ld-linux.so.2 (0xb7728000)


MySQL-shared-compat-6.0.9-0.sles9.i586.rpm

:/opt/ts3server$ ldd libts3db_mysql.so
        linux-gate.so.1 =>  (0xb7809000)
        libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15 (0xb7619000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb752e000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7503000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb74e5000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7369000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb734e000)
        libcrypt.so.1 => /lib/i386-linux-gnu/libcrypt.so.1 (0xb731d000)
        libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xb7303000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb72ee000)
        /lib/ld-linux.so.2 (0xb780a000)


unknown

:/opt/ts3server$ ldd libts3db_mysql.so
        linux-gate.so.1 =>  (0xb7859000)
        libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15 (0xb7669000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb757e000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7553000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb7535000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb73b9000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb739e000)
        libcrypt.so.1 => /lib/i386-linux-gnu/libcrypt.so.1 (0xb736d000)
        libnsl.so.1 => /lib/i386-linux-gnu/libnsl.so.1 (0xb7353000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb733e000)
        /lib/ld-linux.so.2 (0xb785a000)

```

Ok, first person to suggest something that works gets a beer (or cup of coffee) on me!

And for the last and latest attempt on a completely and totally new fresh install:


```
TeamSpeak Server 3.0.0 [Build: 14957]
(c)TeamSpeak Systems GmbH

Logging started
2011-11-04 23:03:50.803454|INFO    |ServerLibPriv |   | Server Version: 3.0.0 [Build: 14957], Linux
2011-11-04 23:03:50.804764|INFO    |DatabaseQuery |   | Please make sure you use the supplied ts3server_minimal_runscript.sh to run the server, or set LD_LIBRARY_PATH yourself
2011-11-04 23:03:50.805275|CRITICAL|DatabaseQuery |   | unable to load database plugin library "libts3db_mysql.so", halting!
```

On a side note, i've apparently lost my last username from this forum as i cant recall what email i had it linked to, and probably to one i dont have access to anymore. =(  Pardon the new username and first post question =D

---

### Post by CorrupterTheLost on 2011-11-09
Any thoughts?  i'm kind of at the end of my wits here.

---

### Post by coder4life.dev on 2011-11-09
I am in a similar boat, same Ubuntu version.

---

### Post by CorrupterTheLost on 2011-11-09
> I am in a similar boat, same Ubuntu version.

Are you also running the same TS3 version coder?

I'm going to continue to tinker with some of the permissions, i'm thinking it could be a permissions issue, although the dependencies are there one of the files might not have the correct permissions.  

Anyone else have any thoughts about this or where i should start?

If i get a result Coder i'll let you know.

---

### Post by coder4life.dev on 2011-11-09
Yes I am running the same Teamspeak 3 Server version.

From what I was reading, it has something to do with the library mysqlclient.so.15 missing in Ubuntu 11.10 version, which Teamspeak Server seems to depend on.  For anyone else reading, this is only a problem with trying to use MySql DB instead of SqlLite DB

---

### Post by CorrupterTheLost on 2011-11-10
Coder,

I am aware of the fact that this particular file isnt included in the latest release of ubuntu, the fix for this is to find the package either manually in the archives and install it or to add an archive package source and use apt-get to then grab it.  To do that here is some basic instructions:

[http://forum.teamspeak.com/showthread.php/47011-How-to-quot-properly-quot-install-TS3-using-a-mySQL-5-server-on-linux.../page3](http://forum.teamspeak.com/showthread.php/47011-How-to-quot-properly-quot-install-TS3-using-a-mySQL-5-server-on-linux.../page3)

if you are looking for other resources to this problem here are the other posts i found on the official ts3 forum, the one above i posted a solution i found a year or so ago but it doesnt seem to be working for me, maybe you will have better luck.  

[http://forum.teamspeak.com/showthread.php/50353-libmysqlclient.so.15-required-but-libmysqlclient.so.16-installed-shared-host](http://forum.teamspeak.com/showthread.php/50353-libmysqlclient.so.15-required-but-libmysqlclient.so.16-installed-shared-host)

[http://forum.teamspeak.com/showthread.php/68912-Help-needed-TS3-x86-installation-on-Ubuntu-11.10-(oneiric](http://forum.teamspeak.com/showthread.php/68912-Help-needed-TS3-x86-installation-on-Ubuntu-11.10-(oneiric)) (this one a guy got it working on 11.10 but it was 64bit the post indicates 32bit but if you read the post the guy realized his problem was he was using the wrong version.)

[http://forum.teamspeak.com/showthread.php/49667-how-to-use-it-with-mysql/page2?highlight=failed+error%3A+Access+denied+user](http://forum.teamspeak.com/showthread.php/49667-how-to-use-it-with-mysql/page2?highlight=failed+error%3A+Access+denied+user)

[http://forum.teamspeak.com/showthread.php/50607-unable-to-load-database-plugin-library-halting](http://forum.teamspeak.com/showthread.php/50607-unable-to-load-database-plugin-library-halting)!

[http://forum.teamspeak.com/showthread.php/46762-Error-Msg-quot-unable-to-load-database-plugin-quot?p=201792#post201792](http://forum.teamspeak.com/showthread.php/46762-Error-Msg-quot-unable-to-load-database-plugin-quot?p=201792#post201792)

Good luck, i've tried all these posts / solutions / and no luck.

---

### Post by coder4life.dev on 2011-11-10
So I solved this through unconventional methods, but it works.  However as a warning do so at your own risk, and make sure you are not overwriting newer packages you have installed with older ones.  This might be just a good method to get the 32bit binary, which I found many were mislabeled as when I searched the internet  as 64 bit. 

Requirements
Ubuntu 11.10
Teamspeak-Server 3.00

First lets modify the source file.  Add this line at the end:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

(NOTE: you cannot remove this afterward, upon next update you will loose the package that was installed)


Lets do an update to the repository listings
apt-get update


Now lets pull an old package installer (make sure you do not have conflicts)
apt-get install libmysqlclient15off
y


Let us check the Mysql Library is there:
cd /usr/lib/
ls libmysql[Key:Tab][Key:Tab]

libmysqlclient.so.15
libmysqlclient.so.15.0.0


Now let us check if the library is found in Teamspeak installed directory
cd /home/temspeak/ts3/
ldd libts3db_mysql.so

(first line) : libmysqlclient.so.15 => /usr/lib/libmysqlclient.so.15


And Start
./ts3server_minimal_runscript.sh inifile=ts3server.ini

---

### Post by CorrupterTheLost on 2011-11-11
Turned out to be a permissions issue.  chmod 755 the directory and making sure to chown username:username the entire directory was important, furthermore on first run the program tries to create some new databases and what not in the folder you are running the program from so make sure user has write permissions to that folder most of all.

---

