---
title: "Oracle on Ubuntu"
date: 2005-02-23
forum: General Help
---

### Post by dstrebel on 2005-02-23
I need to install Oracle 10g or 9i doesn't matter it is for a class I am taking. If anybody has any iformation or links on this it would be greatly appreciated.

---

### Post by halsbge on 2005-02-24
Hi,  I want to do the same thing here.
Did you get any response?

---

### Post by dstrebel on 2005-02-27
I didn't get any responses yet I did find this guide.
[oracle on debian guide](http://www.the-love-shack.net/oracle-on-sid.html) 

I am going to try it out in the next couple days and I will let you know of my prgress

---

### Post by arvindkst on 2005-03-28
Here is a good place to start >> [http://www.togaware.com/linux/survivor/Getting_Oracle.shtml](http://www.togaware.com/linux/survivor/Getting_Oracle.shtml)

I have got Oracle DB and AS running on 6 machines and have had no problems >> not even rebooted the machines in the last 6 months.

A few things you could do different from the guide 

1. Set the ulimit in the profiles
2. Set env variables in the .profiles 
3. In the startup remember to add a line to start the dbconsole 

Let me know if you guys have a problem

---

### Post by Magneto on 2005-05-05
[QUOTE=arvindkst]Here is a good place to start >> [http://www.togaware.com/linux/survivor/Getting_Oracle.shtml](http://www.togaware.com/linux/survivor/Getting_Oracle.shtml)

I have got Oracle DB and AS running on 6 machines and have had no problems >> not even rebooted the machines in the last 6 months.

A few things you could do different from the guide 

1. Set the ulimit in the profiles
2. Set env variables in the .profiles 
3. In the startup remember to add a line to start the dbconsole 

Let me know if you guys have a problem[/QUOTE]
 that link is dead for me anyone have similar info or an updated link?

Thanks much in advance

---

### Post by saif007 on 2005-06-08
Hello,

i am on ubunt 64 bit and i want to install Oracle 9i letest release but wen i run cpio command an error occurs:

cpio: warning: skipped 549148535 bytes of junk
cpio: Memory exhausted


what is the probleme? is somme one have the sme probleme?

---

### Post by atilasendil on 2005-08-01
Hi all;

after installing ubuntu at home a few weeks ago and being so happy I decided to try it at work too.
And the problem is the boss doesn't trust linux about Oracle and I want to show him that linux and particularly ubuntu is as good as the commertial OS :-)
so I have to install Oracle DB on a PC here;

can anyone with experience write a "HOWTO: Install Oracle DB on Ubuntu" ?

please ???

---

### Post by Magneto on 2005-08-01
[QUOTE=atilasendil]Hi all;

after installing ubuntu at home a few weeks ago and being so happy I decided to try it at work too.
And the problem is the boss doesn't trust linux about Oracle and I want to show him that linux and particularly ubuntu is as good as the commertial OS :-)
so I have to install Oracle DB on a PC here;

can anyone with experience write a "HOWTO: Install Oracle DB on Ubuntu" ?

please ???[/QUOTE]
 you are better off using fedora/redhat or suse for oracle - there is alot of support for oracle on those distros and would make more sense for showing your boss

I haven't looked lately for resources but last time I looked there was very little ubuntu oracle stuff out there

---

### Post by gauravtechie on 2005-09-13
Check u have min 1 GB of swap , or increase ur swap

[QUOTE=saif007]Hello,

i am on ubunt 64 bit and i want to install Oracle 9i letest release but wen i run cpio command an error occurs:

cpio: warning: skipped 549148535 bytes of junk
cpio: Memory exhausted


what is the probleme? is somme one have the sme probleme?[/QUOTE]

---

### Post by BigCdaAnswer3 on 2005-09-29
I have written an Oracle 10g guide written exclusively for Ubuntu, which is based off of the debian one, with some changes. You can find it here:

 [http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html](http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html)


Enjoy! :smile:

---

### Post by Eversmann on 2005-10-26
Great guides.

Do you know if that guide for oracle 10 would work for oracle 9i?

that's the version i have to use for the college.

Thanks.

---

### Post by supercleanse on 2005-11-14
I just tried to install Oracel 10g (10.2.0) on Ubuntu Breezy Badger and your tutorial doesn't work. I'm wondering which version of Oracle 10g and Ubuntu you were using...

Thanks.

[QUOTE=BigCdaAnswer3]I have written an Oracle 10g guide written exclusively for Ubuntu, which is based off of the debian one, with some changes. You can find it here:

 [http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html](http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html)


Enjoy! :smile:[/QUOTE]

---

### Post by msinger1 on 2005-11-16
Yeah, his tutorial didn't work for me either on Hoary 5.04 ...

So I tried to install using this: [https://wiki.ubuntu.com/Oracle10g](https://wiki.ubuntu.com/Oracle10g).

Then, I got a problem that says something like "TNS: Lost Contact" during the install.

Did anyone get either of these to work with Ubuntu Hoary 5.04?

---

### Post by ilmw on 2005-11-20
I managed to install Oracle 9i (9.2.0.4) on Ubuntu and Mandrake Linux 10.1. [This]("http://www.fileh.com/ilmw/install.txt") is the installation guide I used (made changes to my own settings. most of the part is based on [here]("http://www.puschitz.com/InstallingOracle9i.shtml"). I also zipped all the prerequisites to a zip file: [here]("http://www.fileh.com/ilmw/readme.zip"). This guide is based on Mandrake linux but all the rpm can be converted to deb by alien. Hope this helps.

[QUOTE=msinger1]Yeah, his tutorial didn't work for me either on Hoary 5.04 ...

So I tried to install using this: [https://wiki.ubuntu.com/Oracle10g](https://wiki.ubuntu.com/Oracle10g).

Then, I got a problem that says something like "TNS: Lost Contact" during the install.

Did anyone get either of these to work with Ubuntu Hoary 5.04?[/QUOTE]

---

### Post by daacon on 2005-11-27
[QUOTE=BigCdaAnswer3]I have written an Oracle 10g guide written exclusively for Ubuntu, which is based off of the debian one, with some changes. You can find it here:

 [http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html](http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html)


Enjoy! :smile:[/QUOTE]

A Big thanks to BigCdaAnswew3 :KS  I just successfully Installed Oracle 10g Release 1 (10.1.0.3) on my recently Installed Ubuntu server. I followed his document with the following (not so much additions more clarifications and  what **I screwed up **the first "couple of times" almost went with a Fedora install ......)

First attempt I already had a user oracle - somehow I lost the sudo rights for this account trying to enable root - as it (ubuntu) is a quick install I re-installed this time creating a different account (typical install)  - I did all this using SUDO and did not enable root. (No need)  - There were no oracle installation errors at all.

For package make sure you also download **lib6bc.dev **for the C header files that are required (link errors will happen if you do not) 

I had to manually download the package lesstif2 (goggled it) as the GUI did not list it. I then installed with sudo dpkg -i <pakage-name.deb>

**be very careful on the symbolic links **- I fat fingered the 'basename' one and got ODBC and emagent errors while oracle was linking  

Do not worry about the Display error as it is checking for a red hat x windows verification choose ignore and installer will fire up fine. Alternatively if you are comfortable that all other prerequisites are met you could run the following: ./runInstaller **-ignoreSysPrereqs **although I do not recommend it

I ran the Advanced Install of Oracle only so I could create the database in a directory of my choosing. I am currently on the Database Configuration Assistant and building my db. 

Even if this fails (it is on the adding Oralce JVM peice now) all Oracle executables are there and there were not installation errors so I can recreate manually. 

That is my story - good luck :smile:

---

### Post by bernardfrancois on 2005-12-11
I'm trying to install oracle (10g, release1) here (ubutnu 5.04).

I can't start the installer. I followed the instructions on the beforementioned websites. It seems that the oracle user can't start any x applications:
```

oracle@ubuntu:~$ xclock
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0

```

I get the same error (but a little more verbose) when running the oracle installer.

Any help would be appreciated a lot...

---

### Post by finster on 2005-12-11
Hi,

Not totally sure on this one, but have you tried "xhost +" (that's a space and a plus sign after the command xhost). This sometimes lets a process running under a different run under X....

---

### Post by bernardfrancois on 2005-12-11
Thanks! it works now, the installer window popped up.

But now connections to the X server are allowed for anyone... Is there a way to set that the oracle user only gets X server acces?

---

### Post by finster on 2005-12-11
Hi,

Does the oracle user really need access to X once oracle has been installed - surely you will just be accessing it via a SQL Net connection or similar.

Otherwise can you not just enable access when you need it.

Have you got security issues granting everybody access to X? You can always limit it to users on your local machine: -

xhost localhost
or xhost +localhost 
or xhost +the_name_of_our_local_machine

I don't really know - perhaps a google of "xhost" will answer your question...

---

### Post by bernardfrancois on 2005-12-12
Thanks finster, I'll check that out later and post it here.
I didn't finish installing yesterday, because the installer said there would be 1.3GB (or more) disk space used, a quantity which is not available on my laptop.

Now I tried on my desktop pc (running ubuntu 5.10). When I want to run the installer, I get the following output:

```

Preparing to launch Oracle Universal Installer from /tmp/OraInstall2005-12-12_03-07-17PM. Please wait ...oracle@linber:/home/ber/oinst/tmp.oinst/oracle$ Exception in thread "main" java.lang.UnsatisfiedLinkError: /tmp/OraInstall2005-12-12_03-07-17PM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1560)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1477)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:506)

```

Note that all other things went fine, and after *xhost +*, the oracle user could run other x applications.

---

### Post by bernardfrancois on 2005-12-15
Now I installed oracle on that laptop anyway (after removing lots of stuff and programs)...

I don't get it to work... 
In fact, I didn't exactly know what to put for the environement variables and stuff.

This is what I tried:

in **/etc/init.d/oracledb**
```

export ORACLE_HOME=/home/oracle/product/10.1.0/Db_1
export ORACLE_SID=biblioth
export PATH=$PATH:$ORACLE_HOME/bin

ORA_OWNR="oracle"

```
I don't know if that owner is correct...
I guessed ORACLE_SID should be the SID of the empty database I created during the setup process..

For the other files:
> 
/usr/local/bin/dbhome needs env. variables ORAHOME, ORASID, and ORATAB (/etc/oratab) changed 
/your/oracle/home/bin/dbhome needs the same as above 
/your/oracle/home/bin/dbshut needs the same as above 
/your/oracle/home/dbstart needs the ORATAB variable changed

I took **ORAHOME** as **/home/oracle/product/10.1.0/Db_1** and **ORASID** as **biblioth** (the SID of the database I created during the installation process).

When I execute **/etc/init.d/oracledb restart**, this might be the part where it goes wrong:
```

SQL*Plus: Release 10.1.0.3.0 - Production on Thu Dec 15 22:46:07 2005

Copyright (c) 1982, 2004, Oracle.  All rights reserved.

SQL> ERROR:
ORA-01031: insufficient privileges


SQL> ORA-01031: insufficient privileges
SQL> 
Database "biblioth" warm started.

```

When I try to start **sqlplus** (logged in as user **oracle**):
```

oracle@ubuntu:~$ sqlplus

SQL*Plus: Release 10.1.0.3.0 - Production on Thu Dec 15 22:56:46 2005

Copyright (c) 1982, 2004, Oracle.  All rights reserved.

Enter user-name: system
Enter password: 
ERROR:
ORA-01034: ORACLE not available
ORA-27101: shared memory realm does not exist
Linux Error: 2: No such file or directory


Enter user-name: 

```

And when I open **[http://localhost.localdomain:5500/em](http://localhost.localdomain:5500/em)** in my browser (I started the browser once as my own user **ber**, once as **oracle**):
> 
Database: bibliotheek
	The database status is currently unavailable. It is possible that the database is in mount or nomount state. Click 'Startup' to obtain the current status and open the database. If the database cannot be opened, click 'Perform Recovery' to perform an appropriate recovery operation.


When I press the apply button, I find a form to fill in a username and password (two times), but I don't know what to use...
> 		
Error Message
Couldnot connect to target database - invalid database credentials	
		
Startup/Shutdown:Specify Host and Target Database Credentials
Specify the following credentials in order to change the status of the database.

During the installation I chose a certain password, and I also chose to unlock all accounts, so oracle wouldn't force me to enter new passwords (because I was scared I might not know the default passwords).
I tried the oracle user name and password, leaving the other fields blank.
I tried the oracle user name and password, ans using 'system' and the password I set for the two other field.
I tried my ubuntu user (ber) with password, leaving the other fields blank...
None of these worked.

Any help would be really appreciated, it's for a big school project (all other students use the windows version)  and the deadline is coming closer...

---

### Post by squidward on 2005-12-17
Wouldn't it be the schizzle if someone made a working deb package install of Oracle.

Legal questions, I know...

I'd take a stab myself, but lack the tech expertise.

---

### Post by bernardfrancois on 2005-12-17
One could make a script to install oracle, or a script to create a .deb package from oracle...
Maybe I can do that, but within two weeks... I'm very busy for school for the moment (monday test bash scripting :)) 

But can anyone help me with my problem? I can't log-in with the password I chose (in fact I don't even know which username to use). More can be read in my previous post. I really need oracle for a school project (we need to write some procedures and triggers in PL/SQL). If I can't get it to work I'll have to install the windows version on Monday...

---

### Post by sitheris on 2005-12-18
[QUOTE=bernardfrancois]One could make a script to install oracle, or a script to create a .deb package from oracle...
Maybe I can do that, but within two weeks... I'm very busy for school for the moment (monday test bash scripting :)) 

But can anyone help me with my problem? I can't log-in with the password I chose (in fact I don't even know which username to use). More can be read in my previous post. I really need oracle for a school project (we need to write some procedures and triggers in PL/SQL). If I can't get it to work I'll have to install the windows version on Monday...[/QUOTE]


Try using sys as sysdba

Or, try this from a terminal window:

sqlplus "/ as sysdba"
startup mount (I think)..or maybe it's just startup

---

### Post by bernardfrancois on 2005-12-19
Thanks mate! It worked... I'm very glad... \\:D/
Funny that I didn't need to enter the password I set before.

This is all I did:
```

sqlplus "/ as sysdba"
startup

```

I would invite you to go and drink a beer, but I guess you don't live anywhere close to Ghent, Belgium...

---

### Post by lnxpwr on 2005-12-22
Hi,
thanx BigCDAnswer,...cool description !
Tried it and found out that libstdc++5 and libc6-dev is also required for 10g on Breezy.
DB works fine ;-)
Greetinx
p.

---

### Post by lnxpwr on 2005-12-22
sqlplus "/as sysdba" needs no passwd when you are the privileged user who installed the db..
Greetinx
p.

---

### Post by lukeage on 2005-12-30
I just downloaded: 10201_database_linux32.zip from the Oracle site - i fell at the first hurdle, it seems they have a way of checking if the OS is supported:

```
Checking operating system version: must be redhat-2.1,
UnitedLinux-1.0 or redhat-3 Failed <<<<
```

However you can get past this by:

```
./runInstaller -ignoreSysPrereqs
```

Now its stuck at 6% and not moving  :(

---

### Post by bernardfrancois on 2006-01-02
Did you try the instructions at [http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html](http://csee.wvu.edu/~ccole/oracle10g-ubuntu.html) ?
I know, they are for the full version of oracle 10g, but the requirements to install it may be the same...

---

### Post by giannisapatis on 2006-02-12
hello,
in your guide you say to **(set your ORACLE_HOME, ORACLE_SID, and PATH variables through the command line or through startup file (i.e. .bashrc))**

as i am new to linux and i dont know how to do it could you please give me your example file.

Thanks in advance ,
giannis

---

### Post by bernardfrancois on 2006-02-12
Those [environement variables](http://en.wikipedia.org/wiki/Environment_variable) can be set by opening the file **~/.bashrc** (~ represents the home directory of your user; like /home/giannisapatis).
There you add the following lines:

```

export ORACLE_HOME="/home/oracle/product/10.1.0/DB_1"
export ORACLE_SID="blabla"
export PATH="/home/oracle/product/10.1.0/Db_1/bin:$PATH"

```

Note that the values of those variables depend on what you chose. Before you set those values you should check if those directories exist. You can do that by executing this in a command line (first do ALT+F2, type xterm, press return): **ls /home/oracle/product/10.1.0/Db_1/bin**. If you get 'No such file or directory', it doesn't exist.
You also have to replace the "blabla" by the SID you chose for your database.

---

### Post by Lod on 2006-02-15
I have a problem with installing Oracle on Ubuntu.
According to the howto's Oracle should install a service called init.cssd. This is not the case when I try to install it.
The message "Expecting the CRS daemons to be up within 600 seconds" which should appear in the console does not appear. No mention in the inittab as well.

I do get two errormessages while installing oracle:
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)

The installations ends succesfull according to the gui.

I'm using Breezy and Oracle 10.2.0. The oracle useraccount isn't my primary useraccount (and has no sudo privileges).
Anybody know what's going wrong?

---

### Post by bernardfrancois on 2006-02-18
I don't know. Maybe you could try again from scratch, there are many steps to take to install it, and if you make a little mistake it might not work...

---

### Post by bmuni on 2006-02-22
I am seeing the same issue as well. init.ccsd is never created. I am noticing this because I am using -ignoresysprereqs which bypasses checking the os version during the install of oracle 10g. This possibly leads to another problem ... rpms are not installed during the installation, and thus the setup scripts for starting oracle is never completed.  Anybody with any ideas on this ... would be greatly appreciated.

---

### Post by Lod on 2006-02-23
I got some installation help from my colleague who used to be our Oracle database administrator. The database is working fine after the installation.
The init.cssd is used for the clustering service. Since I don't plan to use any clustering at home I just leave it at that :) .

[QUOTE=bmuni]I am seeing the same issue as well. init.ccsd is never created. I am noticing this because I am using -ignoresysprereqs which bypasses checking the os version during the install of oracle 10g. [/QUOTE]
I had the same problem. The text mentioned in the wiki to put in /etc/redhat-release is not correct. 
My colleague gave me this text:
```
Red Hat Enterprise Linux AS release 3 (Taroon)
```
This is working (in my case that is). But it doesn't solve the init.cssd problems however, just the use of -ignoresysprereqs.

offtopic:
There is some kind of 'plugin' for Firefox which adds the Oracle documentation to the search bar. Could come in handy I guess.
[http://awads.net/firefox/plugins/oradocs.htm](http://awads.net/firefox/plugins/oradocs.htm)

---

### Post by bernardfrancois on 2006-02-23
I want to uninstall Oracle. Does anyone has an uninstall-script? (if nobody replies, I'll make one myself and post it).

---

### Post by dizwell on 2006-03-16
It is perhaps a bit late for the people in this thread, but I have documented as definitively as I could how to install Oracle 10g Release 2 on Ubuntu 5.10 on [my website]("http://dizwell.com/main/content/view/96/144/").

(Incidentally, I saw someone thinking it an error that they didn't see a message about the 'CRS daemons will be up in 600 seconds', but that's a feature of 10g Release 2, not an error)

Hope it helps someone here, anyway. 

Regards
HJR

---

### Post by marceluda on 2006-03-17
I'm trying to install oracle 10.2.0 for linux x86_64 in my ubuntu 5.10 for x86_64. Following varius of the howtos posted here ( example: [https://wiki.ubuntu.com/Oracle10g]("https://wiki.ubuntu.com/Oracle10g")) I couldn't start the installer.
I get the following error:

```

oracle@seele:/oracle/u01/instalation-image/database$ ./runInstaller -record -destinationFile /home/oracle/responsefile.txt
Iniciando Oracle Universal Installer...

Comprobando requisitos de Installer...

Comprobando la versión del sistema operativo: debe ser redhat-3, SuSE-9, redhat-4, UnitedLinux-1.0, asianux-1 or asianux-2
                                      Aprobado


Se han cumplido todos los requisitos de Installer.

Preparando para iniciar Oracle Universal Installer desde /tmp/OraInstall2006-03-17_11-26-29AM. Espere...oracle@seele:/oracle/u01/instalation-image/database$ Oracle Universal Installer, Versión 10.2.0.1.0 Producción
Copyright (C) 1999, 2005, Oracle. Todos los Derechos Reservados.

Exception java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-03-17_11-26-29AM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory occurred..
java.lang.UnsatisfiedLinkError: /tmp/OraInstall2006-03-17_11-26-29AM/jre/1.4.2/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at oracle.sysman.oii.oiif.oiifm.OiifmGraphicInterfaceManager.<init>(OiifmGraphicInterfaceManager.java:222)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.createInterfaceManager(OiicSessionInterfaceManager.java:193)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.getInterfaceManager(OiicSessionInterfaceManager.java:202)
        at oracle.sysman.oii.oiic.OiicInstaller.getInterfaceManager(OiicInstaller.java:436)
        at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:926)
        at oracle.sysman.oii.oiic.OiicInstaller.main(OiicInstaller.java:866)
Exception in thread "main" java.lang.NoClassDefFoundError
        at oracle.sysman.oii.oiif.oiifm.OiifmGraphicInterfaceManager.<init>(OiifmGraphicInterfaceManager.java:222)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.createInterfaceManager(OiicSessionInterfaceManager.java:193)
        at oracle.sysman.oii.oiic.OiicSessionInterfaceManager.getInterfaceManager(OiicSessionInterfaceManager.java:202)
        at oracle.sysman.oii.oiif.oiifm.OiifmAlert.<clinit>(OiifmAlert.java:151)
        at oracle.sysman.oii.oiic.OiicInstaller.runInstaller(OiicInstaller.java:984)
        at oracle.sysman.oii.oiic.OiicInstaller.main(OiicInstaller.java:866)

```

the problem is with the libs:

```

oracle@seele:/oracle/u01/instalation-image/database$ ldd /tmp/OraInstall2006-03-17_11-26-29AM/jre/1.4.2/lib/i386/libawt.so
        linux-gate.so.1 =>  (0xffffe000)
         => not found
        libjvm.so => not found
        libXp.so.6 => not found
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x5586f000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x558bd000)
        libXtst.so.6 => /usr/lib32/libXtst.so.6 (0x558ca000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x558d0000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x55990000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x559b2000)
        libjava.so => not found
        libc.so.6 => /lib32/tls/libc.so.6 (0x559b5000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x55ae3000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x55aeb000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55b04000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55b07000)
        /lib/ld-linux.so.2 (0x56555000)

```

but the libs not found, like libXp.so.6 or libmlib_image.so exists in other parts of my system and are not recognized even seting de enviroment variable LD_LIBRARY_PATH. Some of the libs are in the oracle install tmp directory:

```

oracle@seele:/oracle/u01/instalation-image/database$ locate libmlib_image.so libjvm.so libXp.so
/tmp/OraInstall2006-03-17_11-26-29AM/jre/1.4.2/lib/i386/libmlib_image.so
/usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
/tmp/OraInstall2006-03-17_11-26-29AM/jre/1.4.2/lib/i386/client/libjvm.so
/tmp/OraInstall2006-03-17_11-26-29AM/jre/1.4.2/lib/i386/server/libjvm.so
/usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
/usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
/usr/lib/libXp.so.6
/usr/lib/libXp.so.6.2.1

```

I know some of the libs I listed are for 64bits and I noted the oracle installer took only 32bits libs . . .( so strange considering that is oracle for x86_64   :-S   )

Do anybody tried oracle on ubuntu64?? Has anybody any idea??

PS: padon for my badly english  :-)

---

### Post by bernardfrancois on 2006-03-18
Are you sure you are trying to install a 64-bit version of oracle?
If it's a 32-bit version, you'll need to install a chrooted environement. More can be read [here](http://ubuntuforums.org/showthread.php?t=24575&highlight=chrooted+environment)

---

### Post by mariuz on 2006-03-30
it works on ubuntu x64 but you need some libs from 32bit version ;)

Here is how it worked for me 
[http://mapopa.blogspot.com/2006/03/installing-oracle-on-ubuntu-breezy.html](http://mapopa.blogspot.com/2006/03/installing-oracle-on-ubuntu-breezy.html)
Original 32 bit version guide is located here (read that first)

[http://www.dizwell.com/main/index.php?option=com_content&task=view&id=96&Itemid=144](http://www.dizwell.com/main/index.php?option=com_content&task=view&id=96&Itemid=144)

---

### Post by DSn0wMan on 2006-04-28
I got 10g R2 to install no problem, once I read the ubuntu wiki ([https://wiki.ubuntu.com/Oracle10g](https://wiki.ubuntu.com/Oracle10g)).

The only problem I have now is connecting via a web browser. 

When I try to connect to [http://localhost.localdomain:1158/em](http://localhost.localdomain:1158/em) or /isql I get a connection refused message.

Also the listenr doesn't apear to starup or shutdown properly.

on startup I get the following errors:

Failed to auto-start Oracle Net Listene using /ade/vikrkuma_new/oracle/bin/tnslsnr

cannot touch `/var/lock/oracle'

on shutdown I get a message - rm: cannot remove `/var/lock/oracle'

Does anyone have any insight into this? I imagine I missed something in the startup script. ](*,)

---

### Post by cali4nian on 2006-08-24
I was trying to install Oracle 9i (9.2.0.1.0) on ubuntu 6 but was keep
getting an error but after applying patch from Oracle metalink

p3006854_9204_LINUX.zip

everything is working normal and all I had to do was ./runInstaller.

there are two version of the patches one for 9i and other one for 10g

install above patch will fix the problem.  :D

Patch readme files said it si for Linux3 but does not really matter.

I installed on my ubuntu.

---

### Post by angela on 2006-08-25
hi all

i'm using oracle express edition in my kubuntu. could somebody explain me how i can import an oracle dump file into it??

regards
Angela

---

### Post by xor007 on 2006-08-29
> **cali4nian said:**
> I was trying to install Oracle 9i (9.2.0.1.0) on ubuntu 6 but was keep
getting an error but after applying patch from Oracle metalink

p3006854_9204_LINUX.zip

everything is working normal and all I had to do was ./runInstaller.

there are two version of the patches one for 9i and other one for 10g

install above patch will fix the problem.  :D

Patch readme files said it si for Linux3 but does not really matter.

I installed on my ubuntu.

Could you please try to post essential steps, I have run oracle 9i on CentOS but don't know how to start with Daper. Don't know which software is required first and which patches are relevant. Don't have a CentOS desktop anymore, but running Oracle 9ir2 on many RHEL 3 servers at work.

Thanx in advance.

---

### Post by xor007 on 2006-08-30
Done! I have 9ir2 running so far so good on Daper.

Started with Desktop Edition, had to run these apt-get:

sudo apt-get update
sudo apt-get install gcc libaio1 lesstif2 lesstif2-dev make rpm libc6 libstdc++5
sudo apt-get install libstdc++2.10-glibc2.2 (bcoz was getting an error related to a similar package). Did all the 9ir2 on linux patches from metalink.

---

### Post by JamesTait on 2006-09-28
> **saif007 said:**
> Hello,

i am on ubunt 64 bit and i want to install Oracle 9i letest release but wen i run cpio command an error occurs:

cpio: warning: skipped 549148535 bytes of junk
cpio: Memory exhausted


what is the probleme? is somme one have the sme probleme?

I'm assuming you copied the cpio command line from index.htm on Installation Disk 1.  I had the same problem and solved it be removing the 'c' from the options, i.e.:

```
cpio -idmv < amd64_db_9204_Disk1.cpio
```

---

### Post by blippy on 2006-11-24
I'm not running X-Windows, so getting access to the home page of Oracle is problematical. I've tried links/links2, and I can log in to the webpage as system with my password, but I can't do anything useful beyond that.

I've done 
apt-get install oracle-xe
and changed my .bashrc:
# oracle initialisation
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE
export PATH

The problem is, when I do
sqlplus / as sysdba
from the command line, I get back
ORA-01031: insufficient privileges

How do I get around this?

---

### Post by blippy on 2006-11-24
Ah, I just tried
sqlplus sys as sysdba
and that let's me in. I'm getting closer.

---

### Post by cantormath on 2006-11-24
> **Magneto said:**
> you are better off using fedora/redhat or suse for oracle - there is alot of support for oracle on those distros and would make more sense for showing your boss

I haven't looked lately for resources but last time I looked there was very little ubuntu oracle stuff out there

you are actually better off using solaris 10...

[One idea...]("http://www.oracle.com/technology/tech/linux/install/index.html")


[Installing Oracle 9i on Linux]("http://tomclegg.net/oracle9i")

---

### Post by blippy on 2006-11-24
> **blippy said:**
> 
How do I get around this?

OK, after some fiddling, I seem to have everything set up. I haven't tried creating new user accounts, and so forth, but I'm pretty confident I'm home-and-dry.

I have taken the trouble to document everything over at
[https://help.ubuntu.com/community/Oracle10g]("https://help.ubuntu.com/community/Oracle10g")

I've done a bit of refactoring of the wikipage (moved the stuff about Breezy to different page), and even included a section about connecting to an Oracle server running on Ubuntu from Windows (:twisted:). It works, and I'm dead chuffed.

---

### Post by troach on 2006-11-24
I got the Oracle Listener to start after I commented out the IPC line.

Does anyone know what change Ubuntu made in Edgy to prevent the listener from starting up a process that utilizes the IPC protocol? I keep getting permission denied.

Thanks,

---

### Post by troach on 2006-11-24
WOW! This worked for me. I made this change to my listener.ora

LISTENER =
  (DESCRIPTION_LIST =
    (DESCRIPTION =
#      (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC_FOR_XE))
      (ADDRESS = (PROTOCOL = IPC)(KEY = IPCKEY))
      (ADDRESS = (PROTOCOL = TCP)(HOST = 127.0.0.1)(PORT = 1521))
    )
  )


If you notice, I made the KEY change from EXTPROC_FOR_XE to IPCKEY. I was able to connect internally doing CONNECT / AS SYSDBA once I set the ORACLE_SID=XE.

---

### Post by sarc on 2006-11-24
I just installed Oracle 10g XE on Edgy without a glitch, following these instructions.  Remember to run the configure command as explained in the tutorial.

[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)



HOWEVER

I am trying to acess the free online server of Oracle 11i at 

[http://vis11510ext5.solutionbeacon.net](http://vis11510ext5.solutionbeacon.net)

But I cannot install and configure J2SE properly!  Forms don't work, I get the message

In order to access this application, you must install the J2SE Plugin version 1.4.2_04 on your client and NPX_PLUGIN_PATH environment variable is set before starting Netscape. To install this plugin, click here to download the oajinit.exe executable. Once the download is complete, double-click the oajinit.exe file to install the plugin. You will be prompted to restart your browser when the installation is complete.

This works perfectly in Windows, but not in Linux!  And what the dickens is a NPX_PLUGIN_PATH anyway?  Please help (I have Java plugin for Firefox already installed).

---

### Post by jagnikam on 2007-04-26
Hi 
actually i m system admin  i m tried lots of time i cant yet exact solution.
PLZ help for Oracle 10g Enterprise Edition Installation On Ubuntu 6.06
Plz send me Installation note on This email ID -- [email]jagnikam@gmail.com[/email]

With  regards 
Jagannth Nikam
:confused: 

> **arvindkst said:**
> Here is a good place to start >> [http://www.togaware.com/linux/survivor/Getting_Oracle.shtml](http://www.togaware.com/linux/survivor/Getting_Oracle.shtml)

I have got Oracle DB and AS running on 6 machines and have had no problems >> not even rebooted the machines in the last 6 months.

A few things you could do different from the guide 

1. Set the ulimit in the profiles
2. Set env variables in the .profiles 
3. In the startup remember to add a line to start the dbconsole 

Let me know if you guys have a problem

---

### Post by harrycalgery on 2007-06-08
:popcorn: I am here

---

### Post by bioShark on 2007-06-13
Hi 
This is a question related to Oracle development under Ubuntu. Or any type of Linux for that matter.
Does anybody know of an IDE for Oracle, SQL, PL/SQL (especially) which works great and has a lot of features under Linux?

P.S. I have to remind you that I am a n00b to Linux, so if my question is out of line, sorry.

---

### Post by DSn0wMan on 2007-06-13
Most people use TORA. The last time I installed it from the repo's it didn't include Oracle Support. You can also use gqlplus for running scripts/queries , and kate or gedit for editing them (both have PL/SQL syntax highlighting).

---

### Post by heyhey on 2007-06-13
Oracle's own SQL Developer works under Ubuntu fine, not a true IDE though.

> **rollandsov said:**
> Hi 
This is a question related to Oracle development under Ubuntu. Or any type of Linux for that matter.
Does anybody know of an IDE for Oracle, SQL, PL/SQL (especially) which works great and has a lot of features under Linux?

P.S. I have to remind you that I am a n00b to Linux, so if my question is out of line, sorry.

---

### Post by bioShark on 2007-06-14
Thanks for your replies.

Oracle's SQL Developer is not the best I have used so far but that will do it. I will also check out: gqlplus, kate and gedit.

Thanks

---

### Post by spyheart on 2007-10-02
The above link isn't working!

Any other sources?

-Pavan

---

### Post by yetkin on 2007-10-03
selam! hi!
you can download the .deb file and install it like any deb package...
you must be a superuser.. and you can use dpkg -i oracle.universal......
then if you have problems try ignore problems because of the sql listener..
use force all parameter then it's done ! just configure it as it tells you after installation!

---

### Post by esmin on 2007-10-22
hi! (we aleykumu selam)

I've downloaded .deb package from Oracle and installed it on freshly installed Kubuntu 7.04 (just after installing nvidia driver). When I start:

sh oracle-xe configure

with root-shell, after asked for port for XE, whatever number I enter (including default value) I receive an error message (error port or something like that)...

any ideas what it might be?

ps. I am linux/ubuntu newbie... so... please be more specific and basic in your answers.

---

### Post by verbero on 2007-11-29
For those searching for how to install Oracle onto Ubuntu, this may help.

[http://www.dizwell.com/prod/node/52](http://www.dizwell.com/prod/node/52)

Howard Dizwell likes using VMWare as well. I'm tempted to get the Dell Ubuntu laptop, install VMWare Workstation and then use various linux distros running under virtual machines to learn and test stuff. Then I won't pollute my 'base' install of Ubuntu.

---

### Post by badwanpk on 2008-05-09
Hello

Previously, i was using an older version of ubuntu. today i upgraded to 8.04. I was using Oracle Enterprize edition 11g R1. I was working perfectly, but after the upgrade the Enterprize Manager is not opening.
displays

Firefox can't establish a connection to the server at 192.168.102.70:1158.
     
        

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

What shall i do.

---

