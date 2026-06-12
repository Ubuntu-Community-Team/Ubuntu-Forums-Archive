---
title: "Teamviewer for Linux as a service"
date: 2010-05-03
forum: General Help
---

### Post by swehes on 2010-05-03
So I have installed the new Teamviewer Beta for Linux onto my computer which is running Ubuntu 10.04. It is working awesome! However right now, if I need for any reason to restart my home computer (ubuntu) I can not logon to my computer again as Teamviewer is down.

So my question is, how can I either
1) setup teamviewer to start as a service as soon as the computer has started, and not me logging in yet. or
2) start teamviewer from command line?

Thanks for any help on the subject.

---

### Post by Bacaryu on 2010-05-03
go to system / preferences / startup applications and add teamviewer to it

---

### Post by swehes on 2010-05-03
Will that allow it to start up before you login? Or do I have to login first? See what I want to do is to be able to restart the computer, remotely, and be able to teamview into the machine without having to have someone login to the computer at home.

---

### Post by xiaokai on 2010-05-03
I tried TV on 10.04 
It lagged the PC when some1 viewed me
Lag on every movement of the mouse

---

### Post by skyline2412 on 2010-05-09
Same problem, the startup applications option just works when somebody login.
Some idea?

---

### Post by dotokija on 2010-05-15
> **skyline2412 said:**
> Same problem, the startup applications option just works when somebody login.
Some idea?
 
[FONT=Palatino Linotype][SIZE=3]You could try to make shell script like this one:[/SIZE][/FONT]

[FONT=Lucida Console][SIZE=2]#!/bin/bash[/SIZE][/FONT]
[FONT=Lucida Console][SIZE=2]/usr/bin/teamviewer[/SIZE][/FONT]

[FONT=Palatino Linotype][SIZE=3]or whatever is the path to the teamviewer executable (I don't recall it right now), save it to:[/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]/etc/init.d/teamviewer_start [/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]and change permission:[/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]chmod 777 /etc/init.d/teamviewer_start [/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]create link:[/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]ln -s /etc/init.d/teamviewer_start /etc/rc5.d/S99teamviewer  [/SIZE][/FONT]

[FONT=Palatino Linotype][SIZE=3]and it should start with the machine regardless of the fact that no user has yet done login.[/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]remark:[/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]/etc/rc5.d/ is the directory where startup scripts are located (default init level is 5, that's why it is named rc5.d). Scripts whose names start with capital "S" are executed in alphabetical order, starting from S00 to S99. [/SIZE][/FONT]
[FONT=Palatino Linotype][SIZE=3]Following the analogy, the directory /etc/rc0.d/ contains stop script executed when machine goes down. Their names begin with "K" starting from K00 to K99.[/SIZE][/FONT]

---

### Post by hornetster on 2010-05-20
Not sure if this can be setup to work prior to login, as it is actually a wine application (ie they are just running the windows application under wine, to get a version for Linux...)
Also, looks like there is a forum has now been setup for TeamViewer (I "think" it's a semi(?)official one) at [http://teamviewerforums.com/index.php](http://teamviewerforums.com/index.php). VERY new - at this stage there is only a handful of posts.
I have asked the question there....
Thanks, John.

---

### Post by howefield on 2010-05-21
> **hornetster said:**
> Also, looks like there is a forum has now been setup for TeamViewer (I "think" it's a semi(?)official one)


Doesn't look the remotest bit official, never mind "semi".

---

### Post by VipSaran on 2010-07-31
Running it as a service haven't helped :(
Finally found the solution for Teamviewer5 not running/starting on ubuntu (10.04):
[http://www.plunk.org/~grantham/cgi-bin/blog.cgi?id=00019](http://www.plunk.org/~grantham/cgi-bin/blog.cgi?id=00019)

---

### Post by milkywayfarer on 2011-03-09
Has anything changed? Is there any possibility to run teamviewer on Ubuntu as service?

---

### Post by Ehknaton on 2011-09-26
Any news yet? Can TeamViewer 6 be started before login? :popcorn:

---

### Post by oldos2er on 2011-09-26
Closed for necromancy.

---

