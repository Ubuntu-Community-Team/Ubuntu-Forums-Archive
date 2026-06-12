---
title: "Gmailwatcher app suddenly stopped working"
date: 2011-07-06
forum: General Help
---

### Post by murlidhar on 2011-07-06
the gmail app gmailwatcher suddenly stopped working and the when run in terminal it gives the following errors. 
the pastebin has been posted here [http://pastebin.com/myb7XshW](http://pastebin.com/myb7XshW)

It was working fine just a few hours back ... when i restarted the pc it stopped working. 
reinstall/reboot/reconfig didn't seem to work at all.

---

### Post by An Sanct on 2011-07-06
Gmail has changed somewhat today. I think it has something to do with Google+.

PS. Even people with push email on their phones have noticed problems...

---

### Post by murlidhar on 2011-07-07
> **An Sanct said:**
> Gmail has changed somewhat today. I think it has something to do with Google+.

PS. Even people with push email on their phones have noticed problems...
Well if gmail was undergoing changes then atleast the app should have started and refused to connect. 
the app doesn't even start now.

---

### Post by kanishkdudeja on 2011-07-07
Well, i don't use gmail watcher..

but i use CheckGmail..its quite handy..

you can check out everything about it at this link..

[http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Its quite handy..works almost perfectly..

if you use ubuntu 11.04 and wish to try out checkgmail..

then follow this thread too..this thread will show you how to resolve a common problem with checkgmail in ubuntu 11.04... 

[http://ubuntuforums.org/showthread.php?t=1710616](http://ubuntuforums.org/showthread.php?t=1710616)

check out post number 9..that shall explain you how to get it working with ubuntu 11.04..

and yeah..if you do start using checkgmail..you can ask me if you encounter any problems..ive fixed a lot of problems with it..so i might be able to help you..

---

### Post by An Sanct on 2011-07-07
Well,

> Did not receive a reply. Possible causes include: the remote application  did not send a reply, the message bus security policy blocked the  reply, the reply timeout expired, or the network connection was broken.

kind of says it all, did you change something in the network settings? Maybe some part of the needed addresses where not present/available ... Maybe you should try again now, it might suddenly work ...

PS. Apps, that handle google mail and are not produced by google will crash and be left without support by google, that is what also the google EULA says.

---

### Post by murlidhar on 2011-07-07
> **An Sanct said:**
> Well,



kind of says it all, did you change something in the network settings? Maybe some part of the needed addresses where not present/available ... Maybe you should try again now, it might suddenly work ...

PS. Apps, that handle google mail and are not produced by google will crash and be left without support by google, that is what also the google EULA says.

no i haven't changed any network settings. 
yes the google eula was stated not yesterday. it was working fine all these months without any problem. 
but yes there were some update done by my update-manager to packages . it definately not included gmailwatcher but others. 
maybe they might have caused some error in python. 
don't know for sure.

---

### Post by murlidhar on 2011-07-07
> **kanishkdudeja said:**
> Well, i don't use gmail watcher..

but i use CheckGmail..its quite handy..

you can check out everything about it at this link..

[http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Its quite handy..works almost perfectly..

if you use ubuntu 11.04 and wish to try out checkgmail..

then follow this thread too..this thread will show you how to resolve a common problem with checkgmail in ubuntu 11.04... 

[http://ubuntuforums.org/showthread.php?t=1710616](http://ubuntuforums.org/showthread.php?t=1710616)

check out post number 9..that shall explain you how to get it working with ubuntu 11.04..

and yeah..if you do start using checkgmail..you can ask me if you encounter any problems..ive fixed a lot of problems with it..so i might be able to help you..


yes. thanks for the advise :) 
but as far as i know checkgmail doesn't not support ubuntu messaging menu. 
and instead runs on a systemtray.

---

### Post by kanishkdudeja on 2011-07-07
yes u're right.

it works on the top right tray.

---

### Post by AnotherMuggle on 2011-07-07
You may like gm-notify: [https://launchpad.net/gm-notify]("https://launchpad.net/gm-notify")

I have tried lots of gmail notification programs, on Ubuntu and a on selection of other Distos. In my opinion gm-notify is easily the best. It's small, simple, fast and integrates beautifully into the Ubuntu messaging menu.

---

### Post by murlidhar on 2011-07-07
> **tomkear2006 said:**
> You may like gm-notify: [https://launchpad.net/gm-notify]("https://launchpad.net/gm-notify")

I have tried lots of gmail notification programs, on Ubuntu and a on selection of other Distos. In my opinion gm-notify is easily the best. It's small, simple, fast and integrates beautifully into the Ubuntu messaging menu.

thanks a lot. i have installed it just now and so far it works beautifully :)

---

### Post by murlidhar on 2011-07-07
I just logged into my other OS maverick and the gmailwatcher works fine there.
:( 
i wonder what happened in natty that is causing this error.

---

### Post by loneowais on 2011-11-03
If you are using Oneiric, you can use this ppa to get new version

ppa:loneowais/gmailwatcher.dev

---

