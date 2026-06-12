---
title: "amaroK crashing"
date: 2006-02-02
forum: General Help
---

### Post by stangbang on 2006-02-02
amaroK cashes when set to random play. It seems to play anywhere from 1-5 songs before it will crash, but it crashes during the switching process.

I am running a clean version of kde 3.5 on breazy (server install, and updated sources.list to include the updated kde source, then installed kde-core, and kdm packages). I have updated to the latest version of amaroK (1.3.8) but the problem still exists. I have tried different sound engines (gstreamer, xine, arts) but I get the same result with every one. I cant realy think of anything else that would be causing this.

Has anyone else had, seen, or know anything to try to fix this problem?


UPDATE********** It is also doing it when set to normal play. Its just nowhere near as often. listened to like 3 1/2 albums before it did it this time.

---

### Post by glycoknob on 2006-02-02
Weird Problem

I'm not quite sure wether this applies to your configuration but it's worth a try.

The amarok version shipped by kde.org or ubuntu depends on taglib 1.4, but taglib 1.3 is installed. 
but amarok needs the new taglib, it crashed here while playing files with certain id3v2 headers. 
I spent far to much time to fiddle it out. However the guys on the irc channel irc.freenode.net #amarok are quite nice ask there if the solution described here won't work.

try the apt-repositories at [www.czessi.net](www.czessi.net) - they are made for the purpose of up to date multi-media stuff for kubuntu. there you will find the new amarok and the correct taglib. besides you'll find there new versions of kaffeine and k3b..

However, the recent security update on libxine broke wma playbay here. downgrade to the former version, which works fine.

[http://security.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1c2_1.0.1-1ubuntu10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xine-lib/libxine1c2_1.0.1-1ubuntu10_i386.deb)

I hope this will help.

martin

---

### Post by stangbang on 2006-02-02
so far it looks like updating the libtag to the new version worked. Will have to bookmark that webpage.

Thanks a bunch for the help. Hopfully dapper will include the new libtag version with it also.

---

### Post by speedothebrief on 2007-03-02
I'm having the same problem with Dapper, I've installed the updates, so far so good... I'll post here after my strenuous testing.... i.e. playing songs through 8 hours at work.

---

### Post by speedothebrief on 2007-03-02
success!
I've now used amarok crash free for the duration of today's workday. Before using the aforementioned repository, I couldn't play more than 25-35 minutes without a crash.

Thanks glycoknob!

---

