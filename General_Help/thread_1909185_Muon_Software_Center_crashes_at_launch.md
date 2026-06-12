---
title: "Muon Software Center crashes at launch"
date: 2012-01-14
forum: General Help
---

### Post by kooldino on 2012-01-14
When I start Muon Software Center, it will crash immediately after launch (segmentation fault).

By contrast, the Muon package manager works fine.

Any ideas on how to fix this?

---

### Post by TeoBigusGeekus on 2012-01-14
Is the message just a segmentation fault or does it provide any more info?

---

### Post by Linforcer on 2012-01-15
It's kind of a mystery. It seems to affect a lot of users, though can't be confirmed very well, so there must be something else influencing it. Hardware or network related issues.

[Ubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/muon/+bug/915235")

There's a [KDE bug report]("https://bugs.kde.org/show_bug.cgi?id=291262"), too but I believe the KDE team is of the general opinion that Ubuntu messed something up to cause this behavior.

In the mean time the command line tools work fine (at least for me) and so does the muon package manager(muon vs. muon-installer)

---

### Post by kooldino on 2012-01-16
Here's the developer information:

```

Application: Muon Software Center (muon-installer), signal: Segmentation fault
[Current thread is 1 (Thread 0xb48aa930 (LWP 14465))]

Thread 2 (Thread 0xb0ea1b70 (LWP 14471)):
#0  0xb73a3fd4 in ?? () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#1  0xb533d88c in g_main_context_prepare () from /lib/i386-linux-gnu/libglib-2.0.so.0
#2  0xb533e637 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0xb533ec2a in g_main_context_iteration () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0xb73a4b37 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#5  0xb73751dd in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#6  0xb7375421 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#7  0xb727890b in QThread::exec() () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#8  0xb7355e2d in ?? () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#9  0xb727b7b3 in ?? () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#10 0xb5424d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#11 0xb5e710ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 1 (Thread 0xb48aa930 (LWP 14465)):
[KCrash Handler]
#7  0xb72cfe11 in QtPrivate::QStringList_contains(QStringList const*, QString const&, Qt::CaseSensitivity) () from /usr/lib/i386-linux-gnu/libQtCore.so.4
#8  0x08066812 in _start ()

```

---

### Post by mastablasta on 2012-01-16
> **Linforcer said:**
> It's kind of a mystery. It seems to affect a lot of users, though can't be confirmed very well, so there must be something else influencing it. Hardware or network related issues.
 
[Ubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/muon/+bug/915235")
 
There's a [KDE bug report]("https://bugs.kde.org/show_bug.cgi?id=291262"), too but I believe the KDE team is of the general opinion that Ubuntu messed something up to cause this behavior.
 
In the mean time the command line tools work fine (at least for me) and so does the muon package manager(muon vs. muon-installer)
 
 
well Muon is Ubuntu's dev crack at Kpackagekit. it is supposed to be a lot faster than kpackagekit. but if it's not working for osme users... i just hope they fix it until LTS. otherwsie it's better to just have kpackagekit.

---

### Post by dale661 on 2012-01-17
> **kooldino said:**
> When I start Muon Software Center, it will crash immediately after launch (segmentation fault).

By contrast, the Muon package manager works fine.

Any ideas on how to fix this?


Mine has been doing the same thing for the past week.  I've went so far as to downloading a the DVD again.  I've burned it to a DVD, and I've loaded it on to USB sticks with Unetbootin and Startup Disk Creator.  It still crashes.

---

### Post by Besugo on 2012-01-17
It's the shortcut. If we set the command as just ```
 muon-installer
``` it works.

---

### Post by woodbyte on 2012-01-17
I tried changing the command from 

muon-installer %i -caption "%c"

to

muon-installer

but it didn't work for me. Still looking for a solution.

---

### Post by woodbyte on 2012-01-17
Is there an alternative to Muon Software Center? I was thinking of KPackage Kit or is that the same as the standard muon package manager?

Any help greatly appreciated.

---

### Post by MoreOrLess on 2012-01-17
synaptic works fine if you don't care about gtk applications not looking perfect in kde.

---

### Post by NerdWermz on 2012-01-17
Brand new install for me with Kubuntu 64bit last night and I am having the same problem.  Wish I found this thread before starting my own.

Here is my error:
> Executable: muon-installer PID: 2032 Signal: Segmentation fault (11)


I do most things from the command line, except i needed something to add the extra repositories as i cannot name them off the top of my head.  so i installed and used synaptic for that in the mean time.

---

### Post by dexan on 2012-01-19
same problem here! uninstalling and installing again isn't working, but muon package manager works fine.

---

### Post by woodbyte on 2012-01-19
Isn't synaptic more or less the same as the standard muon package manager which still works even if the Muon Software Center doesn't?

---

### Post by kooldino on 2012-01-19
> **Besugo said:**
> It's the shortcut. If we set the command as just ```
 muon-installer
``` it works.

Any idea on how to change the shorcut on the old-style launcher menu?  I tried right-clicking, but didn't get the option.

I tried making a desktop shortcut to it as per your instructions, but it still dies.

Also tried this to no avail:

```
kdesudo muon-installer
```

---

### Post by Higlac on 2012-01-22
So I'm a complete linux newbie, but I love how fast and relatively simple it is.

Anyways, I'm having the same issue with Muon, but I don't actually know what alternatives there are, or how to properly install/uninstall them. 

I've had Ubuntu and Kubuntu on another computer and just used the built in package managers for everything. I'm only getting the error on my desktop (fresh install, dual booting Kubuntu 11.10 and Windows 7). Everything works fine on my netbook, which is also running 11.10.

Edit: Everything worked fine. It doesn't work now. Did a recent update break it or something?

---

### Post by MoreOrLess on 2012-01-22
Synaptic is a good alternative:
```
sudo apt-get install --no-install-recommends synaptic
```

If you don't need to install/remove stuff and just want to update, apt-get will do:
```
sudo apt-get update; sudo apt-get dist-upgrade
```

---

### Post by jonashendrickx on 2012-01-25
i am having this issue too... It feels like everything loves to crash in Kubuntu.

I really need a KDE distro for school...

---

### Post by sulyi on 2012-01-26
I do more like muon than synaptic, both are great, but still. Anyway [http://ubuntuforums.org/showpost.php?p=11642354&postcount=3](http://ubuntuforums.org/showpost.php?p=11642354&postcount=3)
and maybe this too [https://bugs.launchpad.net/ubuntu/+source/muon/+bug/915235](https://bugs.launchpad.net/ubuntu/+source/muon/+bug/915235)
cheers

---

### Post by paradigm2 on 2012-02-02
> **jonashendrickx said:**
> i am having this issue too... It feels like everything loves to crash in Kubuntu.

I really need a KDE distro for school...

Yes, I installed Kubuntu after viewing several mixed reviews.  Some suggested it was poor and that Kubuntu is not kept up as well as Ubuntu, others suggested it was fine and rivaled Opensuse's KDE.  It looks like there are some problems.....

This error occured for me after having to interrupt Kubuntu during an update because it stalled at exactly 50%.  I had to go into a terminal and reboot because nothing else was working.  It would just intercept my attempts.  So I did that and got the message tthat it was already in use upon reboot.  So I looked for a lock file.  Found nothing.  Then I tried it again, got the same message, then received a different message about needing to run dpkg.  I did that and then here we are!

---

### Post by songnar on 2012-02-05
songnar@TheHybrid:~$ sudo muon-installer
[sudo] password for songnar: 
Error: "/var/tmp/kdecache-songnar" is owned by uid 1000 instead of uid 0.
songnar@TheHybrid:~$ Error: "/tmp/kde-songnar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-songnar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-songnar" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-songnar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-songnar" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-songnar" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-songnar" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-songnar" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-songnar" is owned by uid 1000 instead of uid 0.
Failed to read classid file: Object not found
KCrash: Application 'muon-installer' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/songnar/.kde/socket-TheHybrid/kdeinit4__0
Error: "/var/tmp/kdecache-songnar" is owned by uid 1000 instead of uid 0.

---

### Post by timswait on 2012-02-06
I get the same problem, used to work fine, now crashes every time and no idea what I've changed :(
```
Executable: muon-installer PID: 3583 Signal: Segmentation fault (11)
```
The 4 digit number after PID: seems different every time. I've tried to report the bug, but it comes up as a commonly reported bug, so I didn't finish submitting the report.

---

### Post by Yellow Pasque on 2012-02-06
The bug is fixed upstream. You'll have to use an alternative package manager (or use the workaround in the bug report) until the fix makes into the oneiric repo.

---

### Post by kooldino on 2012-02-07
> **timswait said:**
> I get the same problem, used to work fine, now crashes every time and no idea what I've changed :(
```
Executable: muon-installer PID: 3583 Signal: Segmentation fault (11)
```
The 4 digit number after PID: seems different every time. I've tried to report the bug, but it comes up as a commonly reported bug, so I didn't finish submitting the report.

The reason the PID number is different is because it should be.

PID means "Process ID".  Each time a new process starts on your machine, it's assigned a random ID number.

---

### Post by cirjanalex on 2012-02-26
Hello , 

I had the same problem but what i did next solved it for me.

- Open Muon Package Manager  - > Settings -> Configure Software Sources.
- Under the Kubuntu Software tab i deselected Proprietary drivers for devices.

After this Muon Software Center opened without crashing.

---

### Post by sonicflash on 2012-03-04
> **cirjanalex said:**
> Hello , 

I had the same problem but what i did next solved it for me.

- Open Muon Package Manager  - > Settings -> Configure Software Sources.
- Under the Kubuntu Software tab i deselected Proprietary drivers for devices.

After this Muon Software Center opened without crashing.
if you cant access "configure software sources" then open up the
 -Kick Off App Launcher and search for Configure Software Sources.
 -then under the Kubuntu Software tab deselect Proprietary drivers for devices.
 -next go under other software and select canonical partner and select that and the canonical partners(source code) it will download some package and then open up the software center and it works.

Hope this works for evveryone else!

---

### Post by Glaciusor on 2012-03-19
I had this too... the thing that got it working for me:
sudo apt-get purge muon
sudo apt-get install muon

In my case at least, my guess is some config that "remove" didn't get rid of, purge did.

Hope that helps someone out there :)

---

### Post by sidesman on 2012-03-21
> **kooldino said:**
> When I start Muon Software Center, it will crash immediately after launch (segmentation fault).

By contrast, the Muon package manager works fine.

Any ideas on how to fix this?

Nyisd meg a Konsole-t, és a terminálban add ki a következ&#337; három parancsot sorban:
 
[LIST]
[*]sudo add-apt-repository ppa:echidnaman/qapt
[*]sudo apt-get update
[*]sudo apt-get dist-upgrade
[/LIST]
ennyi :)

---

### Post by goldshirt9 on 2012-04-19
had the same problem on a **[COLOR=Red]fresh install[/COLOR]** so here is how i got it to work

open muon package manager - settings - configure software sources - (enter password) - 
other software - tick all boxes except cdrom ( mainly conical partners ) - close 

this should reload the system.
open the muon software manager and all ok :P

hope it works

---

### Post by MazeChaZer on 2012-04-22
I had the same problem with Kubuntu 10.10 and I changed the start command in the start menu from 'muon %i -caption "%c"' to 'muon' and Muon worked again. You can also run the command 'muon' in the command line to start it. Hope this helps you ;)

---

### Post by MazeChaZer on 2012-04-22
Oh I think i was wrong here, I thought this thread was about 'muon' and not the 'muon-installer'. Sorry for that.

---

### Post by MazeChaZer on 2012-04-22
Nevertheless, i had the same problem with the muon-installer and the tip of goldshirt9 fixed it. Thank you :)

---

### Post by autusgo on 2012-05-07
> **goldshirt9 said:**
> had the same problem on a **[COLOR=Red]fresh install[/COLOR]** so here is how i got it to work

open muon package manager - settings - configure software sources - (enter password) - 
other software - tick all boxes except cdrom ( mainly conical partners ) - close 

this should reload the system.
open the muon software manager and all ok :P

hope it works

I tried EVERYTHING recommended in the other replies, this was the only thing that worked for me :p

---

### Post by goldshirt9 on 2012-05-07
my pleasure.:)

---

### Post by sulyi on 2012-05-09
Precise Pangolin has a lot update in software center, as I read. I haven’t tried yes, looks promising though, all of the new distro.

---

### Post by wilskye on 2012-08-13
Big thanx to goldshirt9  who helped fixed this dam annoying problem

---

