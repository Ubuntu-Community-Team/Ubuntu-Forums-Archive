---
title: "is Logkeys running or not installed?"
date: 2010-05-15
forum: General Help
---

### Post by UBVirginia on 2010-05-15
hi there, I have                                           after alof of trouble installed logkeys (i think )on my computer, but cant find the file /var/log/logkeys.log

so first of all i would like to get this out of the way, it is on my computer and to monitor what happens on my computer when im not there. no one else should be using it, but i believe there is, so my intensions with this program is simply to prove that. 

so first of all, when i did the install i got: 

$ sudo make install
Making install in src
make[1]: Entering directory `/home/josh/src/build/src'
make[2]: Entering directory `/home/josh/src/build/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c logkeys '/usr/local/bin'
make  install-exec-hook
make[3]: Entering directory `/home/josh/src/build/src'
chown root /usr/local/bin/logkeys
chmod u+s /usr/local/bin/logkeys
make[3]: Leaving directory `/home/josh/src/build/src'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/josh/src/build/src'
make[1]: Leaving directory `/home/josh/src/build/src'
Making install in man
make[1]: Entering directory `/home/josh/src/build/man'
make[2]: Entering directory `/home/josh/src/build/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 ../../man/logkeys.8 '/usr/local/share/man/man8'
make[2]: Leaving directory `/home/josh/src/build/man'
make[1]: Leaving directory `/home/josh/src/build/man'
Making install in scripts
make[1]: Entering directory `/home/josh/src/build/scripts'
make[2]: Entering directory `/home/josh/src/build/scripts'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c ../../scripts/lkl ../../scripts/lklk '/usr/local/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/josh/src/build/scripts'
make[1]: Leaving directory `/home/josh/src/build/scripts'
make[1]: Entering directory `/home/josh/src/build'
make[2]: Entering directory `/home/josh/src/build'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/josh/src/build'
make[1]: Leaving directory `/home/josh/src/build'

the src folder acctually beeing the logkeys0.1.0 folder just renamed.. and i have used this sudo make install command before, maybe that why i get make 2. 

it never asked for my password and i'm simply not sure if its running or not??  when i try to do the recommended tests i get: 

or first i pushed alt+f2 and wrote bin/lkl in there, it is suppose to be the start command.. 

then back in the terminal i wrote :
$ touch test.log
josh@josh-laptop:~/src/build$ logkeys --start --output test.log
logkeys: Another process already running. Quitting.

then its saying to open another terminal and wrote
tail --follow test.log
and gets

2010-05-16 10:26:06+1000 > <LCtrl>v
2010-05-16 10:26:13+1000 > the src folder acctually beeing the logkeys0.1.0 folder just renamed.. and i have j<BckSp>used this sudo make install command before, maybe that why i get make 2. 
2010-05-16 10:27:40+1000 > 
2010-05-16 10:27:40+1000 > it never asked for my password and it <BckSp><BckSp><BckSp>i'm simply not sure if its running or not<RShft>??  when i try to do the recommended tests i get<LShft>: 
2010-05-16 10:28:35+1000 > 
2010-05-16 10:28:36+1000 > bin<Left><Left><Left><Left>/<Right><Right><Right>/lkl
2010-05-16 10:29:43+1000 > bin/lkl
2010-05-16 10:29:50+1000 > touch test.log
2010-05-16 10:30:18+1000 > logkeys --start --output test.log
2010-05-16 10:30:55+1000 > tail --follow test.log
2010-05-16 10:31:32+1000 > or first i pushed alt=<BckSp><RShft>+f2 and wrote bin/lkl in there, it is suppose to be the start command.. 
2010-05-16 10:33:26+1000 > 
2010-05-16 10:33:27+1000 > then back in the terminal i wrote <LShft>:
2010-05-16 10:34:11+1000 > <LCtrl>v
2010-05-16 10:34:18+1000 > then its sying to open another terminal and wrote<Left><#+18><Left><Left><Left>a<End>
2010-05-16 10:35:08+1000 > <LCtrl>v
2010-05-16 10:35:12+1000 > ad<BckSp>nd gets


so there it is obviously logging!! so according to me, wouldnt this mean that the program is running?? 
so when i try to find where the log files are thats when i struggle (or even more maybe i should say)
 
$ file /var/log/logkeys.log
/var/log/logkeys.log: ERROR: cannot open `/var/log/logkeys.log' (No such file or directory)
and i get the same message if i push alt f2 and write /var/log/logkeys.log

have i not installed the program correctly? or is the file somewhere else? this is surpose to be the default place for the logs? or do i not access these files trough the terminal? 

confused! thought i had it all sorted by now.. is it not installed correctly ? where is the logs? :confused:

but while i'm at it, 
will logkeys start up automaticly when i start my computer? 
how can i choose where to save my logs ?if i understood it right i will be able to
have the files sent to an external source, as email? for checking whats going on at
your home computer while not there...
and how do i make sure that the program runs in the background?

would really appreciate some help :smile: but i'm also very new to this so please be gentle

---

### Post by purplepixie on 2010-05-31
Stop logkeys:

logkeys --kill

create log file:

touch /home/me/mylogfile.txt

logkeys --start --output /home/me/mylogfile.txt

check logging:

tail -f /home/me/mylogfile.txt

Easiest way to add it to add to startup is System->Preferences->Startup Applications

logkeys --start --output /home/me/mylogfile.txt

Or add to end of /etc/init.d/rc.local

No current support for email, but you could write a script to do it, like curl example posted on their
[http://code.google.com/p/logkeys/issues/detail?id=24#c1](http://code.google.com/p/logkeys/issues/detail?id=24#c1)

---

### Post by UBVirginia on 2010-07-06
YES!!!

sorry for taking so long to get back to you, and THANK you, working like a charm :))

cheers!

i would mark this as solved if i just knew how :)

---

### Post by SummerVocal on 2012-11-20
> **purplepixie said:**
> 

Easiest way to add it to add to startup is System->Preferences->Startup Applications

logkeys --start --output /home/me/mylogfile.txt

Or add to end of /etc/init.d/rc.local



Just two remarks : 

- System->Preferences->Startup Applications only applies to the current user gnome session. It won't work for other users, unless you set the same parameter for them.

- AFAIK, the right file to update is /etc/rc.local. /etc/init.d/rc.local is a startup script that uses /etc/rc.local

---

### Post by wildmanne39 on 2012-11-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

