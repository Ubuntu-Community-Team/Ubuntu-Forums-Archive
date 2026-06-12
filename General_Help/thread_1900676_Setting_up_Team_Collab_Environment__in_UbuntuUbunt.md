---
title: "Setting up Team Collab Environment  in Ubuntu/Ubuntu Server"
date: 2011-12-26
forum: General Help
---

### Post by paragoniq on 2011-12-26
Hi guys,

I wanna set up a workspace for my team. We're gonna use Eclipse as our IDE and want to be able to share documents, calendars, etc. 

I want my team to be able to connect to the same Ubuntu instance - sorta like Remote Desktop for everybody- the reason being we wanna keep a local repository in the server/PC. This way, we can each log on to our own account, read any updates, share content, code and commit, and it''ll all be synced up.

Given that we don't wanna use any online reps or content managers, how can I accomplish this?

Install Ubuntu server? Is there a how-to? Do I need a powerful PC or a server? 
The cheaper the better.

Basically, I just wanna have a team HQ where everything is synced up and we can be connected simultaneously.

Team size is 4-6 dudes.


Thanks!

---

### Post by paragoniq on 2011-12-27
Bump

---

### Post by Synoc on 2011-12-27
> **paragoniq said:**
> Hi guys,

I wanna set up a workspace for my team. We're gonna use Eclipse as our IDE and want to be able to share documents, calendars, etc. 

I want my team to be able to connect to the same Ubuntu instance - sorta like Remote Desktop for everybody- the reason being we wanna keep a local repository in the server/PC. This way, we can each log on to our own account, read any updates, share content, code and commit, and it''ll all be synced up.

Given that we don't wanna use any online reps or content managers, how can I accomplish this?

Install Ubuntu server? Is there a how-to? Do I need a powerful PC or a server? 
The cheaper the better.

Basically, I just wanna have a team HQ where everything is synced up and we can be connected simultaneously.

Team size is 4-6 dudes.


Thanks!

remember that Ubuntu server is CLI based not GUI. if you all want to remote in to a shared desktop it will be a CLI. If you want to VNC in or ssh then you can all have a separate instance each on the same PC/Server. 

Are you planning on working on the same document at the same time? like on online "whiteboard" program? if so, that's well beyond me sorry. but I figured I'd help you get the ball rolling.
there are several online collaborative program (some cost) some are free. [http://www.dabbleboard.com](http://www.dabbleboard.com) has a free one and a paid one.

Let's start there

---

### Post by Lars Noodén on 2011-12-27
I would use an old machine.  Neither SVN or Git require a lot of system resources.  Nor does source code take a lot of disk space.  

You can do a lot of file sharing with SSH if you set up SSHFS, too.  The remote machine will appear as a local folder.

As far as calendar servers go, you could look at these three:

Kolab
    [http://www.kolab.org/](http://www.kolab.org/)
Citadel
    [http://www.citadel.org/](http://www.citadel.org/)
Bedework
    [http://www.bedework.org/](http://www.bedework.org/)

They give a lot more than just calendars, but there's no obligation to use the extra stuff and probably it can be easily removed or turned off.

---

