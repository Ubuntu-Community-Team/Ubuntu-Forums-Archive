---
title: "software install broken! Help!"
date: 2010-06-08
forum: General Help
---

### Post by Dee_Ann on 2010-06-08
Hi,

Somehow the software install stuff is broken.

Last week or so I got a notice that updates were available.  I told it to install them.  It started doing so then just hung up and would not finish.  After about 8 hour I tried to kill the windows but they wouldn't close so I ended up having to reboot.  It's not been right since then.

If I try to install *anything* by any method and I get this error,

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Ok, so I open a terminal window and I do exactly what it says.
This is what it does,

> dee@Xena:~$ sudo dpkg --configure -a
[sudo] password for dee: 
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
^X^Z
[1]+  Stopped                 sudo dpkg --configure -a
dee@Xena:~$ 




From that point on the pc is almost dead stopped, the dpkg program runs forever taking up about 98% of the CPU.

Even though it says the program is stopped, it is not, I have to use the system monitor to kill the program.

It makes it very hard to do anything.

I left it running for THREE DAYS like that and it never slowed down.  The disc light doesn't flicker so it's not doing anything to the disc.  All it does is eat up the CPU so I can't do anything else.

:confused:


Please help!  I can't fix this and there's other things that are messed up that I can't fix until this is cleared.
Oh yes, I am using 64bit if that matters.

Thank you!

---

### Post by davidmohammed on 2010-06-08
try the following in a terminal 

sudo mv /var/lib/dpkg/info/libopenal1.* /tmp

then

 sudo dpkg --configure -a

---

### Post by Dee_Ann on 2010-06-08
> **davidmohammed said:**
> try the following in a terminal 

sudo mv /var/lib/dpkg/info/libopenal1.* /tmp

then

 sudo dpkg --configure -a


Same thing.  CPU is at 98% and stuck in a loop.  :(

---

### Post by davidmohammed on 2010-06-08
is it trying to "setup" some-other package other than libopenal1 ?

if it is repeat the command by substitute libopenal1 with the package name

i.e.

sudo mv <packagename>.* /tmp

sudo dpkg --configure -a

---

### Post by Dee_Ann on 2010-06-08
> **davidmohammed said:**
> is it trying to "setup" some-other package other than libopenal1 ?

if it is repeat the command by substitute libopenal1 with the package name

i.e.

sudo mv <packagename>.* /tmp

sudo dpkg --configure -a


Um, I have no earthly clue.  I am not computer savvy or a programmer.

> dee@Xena:~$ 
dee@Xena:~$ sudo mv /var/lib/dpkg/info/libopenal1.* /tmp
mv: cannot stat `/var/lib/dpkg/info/libopenal1.*': No such file or directory
dee@Xena:~$ 
dee@Xena:~$ 
dee@Xena:~$ sudo dpkg --configure -a
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
^Z
[1]+  Stopped                 sudo dpkg --configure -a
dee@Xena:~$ 
I'm just a casual user bumbling through this.  :(

edit:  I bumbled into the system logs and found this,
> 2010-06-08 14:34:54 startup packages configure
2010-06-08 14:34:54 configure libopenal1 1:1.12.854-0ubuntu1~lucid1 1:1.12.854-0ubuntu1~lucid1
2010-06-08 14:34:54 status unpacked libopenal1 1:1.12.854-0ubuntu1~lucid1
2010-06-08 15:36:53 startup packages configure
2010-06-08 15:36:54 configure libopenal1 1:1.12.854-0ubuntu1~lucid1 1:1.12.854-0ubuntu1~lucid1
2010-06-08 15:36:54 status unpacked libopenal1 1:1.12.854-0ubuntu1~lucid1
2010-06-08 15:48:59 startup packages configure
2010-06-08 15:48:59 configure libopenal1 1:1.12.854-0ubuntu1~lucid1 1:1.12.854-0ubuntu1~lucid1
2010-06-08 15:48:59 status unpacked libopenal1 1:1.12.854-0ubuntu1~lucid1
and

> 
Jun  8 14:25:36 Xena AptDaemon: INFO: InstallPackages() was called: dbus.Array([dbus.String(u'virtualbox-ose-qt')], signature=dbus.Signature('s'))
Jun  8 14:25:41 Xena AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/b0d49486181b49cbbc3e7ba9ef33ff03
Jun  8 14:25:41 Xena AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/b0d49486181b49cbbc3e7ba9ef33ff03
Jun  8 14:25:41 Xena AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/b0d49486181b49cbbc3e7ba9ef33ff03
Jun  8 14:26:38 Xena AptDaemon: INFO: UpdateCache() was called
Jun  8 14:26:42 Xena AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/cb8a300640c642c6b52c0116b633f10f
Jun  8 14:26:42 Xena AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/cb8a300640c642c6b52c0116b633f10f
Jun  8 14:26:42 Xena AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/cb8a300640c642c6b52c0116b633f10f
Jun  8 14:32:28 Xena AptDaemon: INFO: Quiting due to inactivity
Jun  8 14:32:28 Xena AptDaemon: INFO: Shutdown was requested

and

> Jun  8 14:25:40 Xena polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:dee to gain TEMPORARY authorization for action org.debian.apt.install-packages for system-bus-name::1.167 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:dee)
Jun  8 14:26:01 Xena sudo:      dee : TTY=unknown ; PWD=/home/dee ; USER=root ; COMMAND=/usr/bin/software-properties-gtk -n -t 71303333
Jun  8 14:26:42 Xena polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session2 successfully authenticated as unix-user:dee to gain TEMPORARY authorization for action org.debian.apt.update-cache for system-bus-name::1.167 [/usr/bin/python /usr/bin/software-center] (owned by unix-user:dee)
Jun  8 14:26:44 Xena dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.167" (uid=1000 pid=11065 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.171" (uid=0 pid=11147 comm="/usr/bin/python))
Jun  8 14:26:56 Xena sudo:      dee : TTY=unknown ; PWD=/home/dee ; USER=root ; COMMAND=/usr/sbin/synaptic
Jun  8 14:31:55 Xena sudo:      dee : TTY=unknown ; PWD=/home/dee ; USER=root ; COMMAND=/usr/sbin/synaptic
Jun  8 14:34:54 Xena sudo:      dee : TTY=pts/0 ; PWD=/home/dee ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a
Jun  8 14:36:45 Xena sudo:      dee : TTY=unknown ; PWD=/home/dee ; USER=root ; COMMAND=/bin/kill -s 9 11526
Jun  8 15:17:01 Xena CRON[12943]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  8 15:17:02 Xena CRON[12943]: pam_unix(cron:session): session closed for user root
Jun  8 15:36:47 Xena sudo:      dee : TTY=pts/0 ; PWD=/home/dee ; USER=root ; COMMAND=/bin/mv /var/lib/dpkg/info/libopenal1.conffiles /var/lib/dpkg/info/libopenal1.list /var/lib/dpkg/info/libopenal1.md5sums /var/lib/dpkg/info/libopenal1.postinst /var/lib/dpkg/info/libopenal1.postrm /var/lib/dpkg/info/libopenal1.shlibs /tmp
Jun  8 15:36:53 Xena sudo:      dee : TTY=pts/0 ; PWD=/home/dee ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a
Jun  8 15:38:19 Xena sudo:      dee : TTY=unknown ; PWD=/home/dee ; USER=root ; COMMAND=/bin/kill -s 9 13614
Jun  8 15:48:42 Xena sudo:      dee : TTY=pts/0 ; PWD=/home/dee ; USER=root ; COMMAND=/bin/mv /var/lib/dpkg/info/libopenal1.* /tmp
Jun  8 15:48:47 Xena sudo:      dee : TTY=pts/0 ; PWD=/home/dee ; USER=root ; COMMAND=/bin/mv /var/lib/dpkg/info/libopenal1.* /tmp
Jun  8 15:48:59 Xena sudo:      dee : TTY=pts/0 ; PWD=/home/dee ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a
Jun  8 15:50:42 Xena sudo:      dee : TTY=unknown ; PWD=/home/dee ; USER=root ; COMMAND=/bin/kill -s 9 14030


---

### Post by davidmohammed on 2010-06-08
...
 scratching my head...

the mv command means move the file from one location to another.

the error message means it cannot see any files in that directory beginning with libopenal1

just wondering if 64bit ubuntu has its dpkg directory in a different file location

can you open your file browser and see if you can navigate to

/var/lib/dpkg/info

if you can, is there any files beginning with libopenal1

---

### Post by Dee_Ann on 2010-06-08
> **davidmohammed said:**
> ...
 scratching my head...

the mv command means move the file from one location to another.

the error message means it cannot see any files in that directory beginning with libopenal1

just wondering if 64bit ubuntu has its dpkg directory in a different file location

can you open your file browser and see if you can navigate to

/var/lib/dpkg/info

if you can, is there any files beginning with libopenal1


This is what I get when I ls the directory.

> dee@Xena:~$ 
dee@Xena:~$ ls -l /var/lib/dpkg/info/libopenal*
ls: cannot access /var/lib/dpkg/info/libopenal*: No such file or directory
dee@Xena:~$ 
dee@Xena:~$ 
 
There are lots of other files in there however.

> dee@Xena:~$ 
dee@Xena:~$ ls -l /var/lib/dpkg/info/libope*
-rw-r--r-- 1 root root  290 2010-05-01 22:01 /var/lib/dpkg/info/libopencore-amrnb0.list
-rw-r--r-- 1 root root  313 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrnb0.md5sums
-rwxr-xr-x 1 root root  135 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrnb0.postinst
-rwxr-xr-x 1 root root  132 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrnb0.postrm
-rw-r--r-- 1 root root   39 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrnb0.shlibs
-rw-r--r-- 1 root root  290 2010-05-01 22:01 /var/lib/dpkg/info/libopencore-amrwb0.list
-rw-r--r-- 1 root root  313 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrwb0.md5sums
-rwxr-xr-x 1 root root  135 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrwb0.postinst
-rwxr-xr-x 1 root root  132 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrwb0.postrm
-rw-r--r-- 1 root root   39 2009-09-28 11:23 /var/lib/dpkg/info/libopencore-amrwb0.shlibs
-rw-r--r-- 1 root root  390 2010-04-29 07:34 /var/lib/dpkg/info/libopenexr6.list
-rw-r--r-- 1 root root  560 2009-11-23 16:56 /var/lib/dpkg/info/libopenexr6.md5sums
-rwxr-xr-x 1 root root  135 2009-11-23 16:56 /var/lib/dpkg/info/libopenexr6.postinst
-rwxr-xr-x 1 root root  132 2009-11-23 16:56 /var/lib/dpkg/info/libopenexr6.postrm
-rw-r--r-- 1 root root   35 2009-11-23 16:56 /var/lib/dpkg/info/libopenexr6.shlibs
-rw-r--r-- 1 root root 1689 2010-05-02 03:08 /var/lib/dpkg/info/libopengl-perl.list
-rw-r--r-- 1 root root 2547 2009-12-12 13:44 /var/lib/dpkg/info/libopengl-perl.md5sums
-rw-r--r-- 1 root root  256 2010-05-01 22:01 /var/lib/dpkg/info/libopenjpeg2.list
-rw-r--r-- 1 root root  291 2009-04-30 01:25 /var/lib/dpkg/info/libopenjpeg2.md5sums
-rwxr-xr-x 1 root root  135 2009-04-30 01:24 /var/lib/dpkg/info/libopenjpeg2.postinst
-rwxr-xr-x 1 root root  132 2009-04-30 01:24 /var/lib/dpkg/info/libopenjpeg2.postrm
-rw-r--r-- 1 root root   27 2009-04-30 01:24 /var/lib/dpkg/info/libopenjpeg2.shlibs
-rw-r--r-- 1 root root  254 2010-04-29 07:32 /var/lib/dpkg/info/libopenobex1.list
-rw-r--r-- 1 root root  289 2010-03-06 14:19 /var/lib/dpkg/info/libopenobex1.md5sums
-rwxr-xr-x 1 root root  135 2010-03-06 14:19 /var/lib/dpkg/info/libopenobex1.postinst
-rwxr-xr-x 1 root root  132 2010-03-06 14:19 /var/lib/dpkg/info/libopenobex1.postrm
-rw-r--r-- 1 root root   27 2010-03-06 14:19 /var/lib/dpkg/info/libopenobex1.shlibs
dee@Xena:~$ 


When I checked to see if it moved the files to the /tmp directory, they are there.

> dee@Xena:~$ ls -l /tmp/libopenal*
-rw-r--r-- 1 root root  24 2010-05-13 15:40 /tmp/libopenal1.conffiles
-rw-r--r-- 1 root root 336 2010-06-04 13:11 /tmp/libopenal1.list
-rw-r--r-- 1 root root 299 2010-05-13 15:40 /tmp/libopenal1.md5sums
-rwxr-xr-x 1 root root 135 2010-05-13 15:40 /tmp/libopenal1.postinst
-rwxr-xr-x 1 root root 132 2010-05-13 15:40 /tmp/libopenal1.postrm
-rw-r--r-- 1 root root  23 2010-05-13 15:40 /tmp/libopenal1.shlibs
dee@Xena:~$ 


---

### Post by davidmohammed on 2010-06-08
ok
  try 

sudo dpkg --clear-avail

this should forget what is available to install

then do

sudo apt-get update

---

### Post by Dee_Ann on 2010-06-08
I swear, I did not touch the keyboard while this was running but here are the results

> dee@Xena:~$ 
dee@Xena:~$ sudo dpkg --clear-avail
[sudo] password for dee: 
dee@Xena:~$ 
dee@Xena:~$ 
dee@Xena:~$ 
dee@Xena:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]                         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                                               
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages                                         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [189B]                                
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [38.5kB]    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [31.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [10.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [2,013B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages           
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [13.8kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [192kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [2,096B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [737B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [75.3kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [12.8kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [47.2kB]                                 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [632B]                                 
Fetched 467kB in 7s (65.0kB/s)                                                                               
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dee@Xena:~$ 
dee@Xena:~$ sudo dpkg --configure -a
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...



And right back to being stuck at full CPU again..  :(  :confused:

---

### Post by davidmohammed on 2010-06-09
ok - last try from me ... if these don't work hopefully someone else can pitch in!

Please check in your software sources that you are not using third party repositories (uncheck anything in the "other" tab)

also try reconfiguring just the package causing the issue i.e.

sudo dpkg --configure libopenal1

then 

sudo apt-get -f install

followed by

sudo apt-get update

---

### Post by Dee_Ann on 2010-06-09
> **davidmohammed said:**
> ok - last try from me ... if these don't work hopefully someone else can pitch in!

Please check in your software sources that you are not using third party repositories (uncheck anything in the "other" tab)

also try reconfiguring just the package causing the issue i.e.

sudo dpkg --configure libopenal1

then 

sudo apt-get -f install

followed by

sudo apt-get update


Step one = fail.  :confused:


> 
dee@Xena:~$ sudo dpkg --configure libopenal1
[sudo] password for dee: 
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
Killed
dee@Xena:~$ 



As usual, dpkg runs without end at 98% CPU and continues to do so until I kill the program.  :(


I guess it's broken beyond repair.

I suppose I should buy a new drive and install a brand new fresh copy.

This one has never been right since I upgraded from the 9.04 to 9.10 then to 10.04.

It's been a long, painful chain of problems.  :(

---

