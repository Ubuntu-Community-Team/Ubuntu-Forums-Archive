---
title: "Stuck at Splash Screen"
date: 2012-05-24
forum: General Help
---

### Post by sagar_aarya on 2012-05-24
Hi frnds


I installed XMMS2 in my ubuntu
I am using UBUNTU 10.04


After installing,and Playing one song
My laptop is working weird,

So I restarted it,
after that ,There was no login screen .

I uninstalled XMMS2 
I upgraded my ubuntu.

Still the Problem is there.

Please Help guys,

This is second time,i came across this kind of problem

I formatted my ubuntu First time..... :( :( :(


[B]uname -r 
2.6.32-41-generic
[/B]

[B]screen is stucked like this(NO LOGIN OPTIONS)
[/B]
[http://www.sucka.net/wp-content/uploads/2010/03/boot.png?cda6c1](http://www.sucka.net/wp-content/uploads/2010/03/boot.png?cda6c1) 


Thanks

---

### Post by fantab on 2012-05-24
Since you already formatted Ubuntu, tell us if you have a separate /home and did you format that too?

If you haven't then there could old XMMS2 configuration file present that are causing the problem... 
In that case, do have any valuable DATA on /home that you wish to preserve? 
If not, then I suggest you upgrade to Ubuntu 12.04 and format /home as well.

---

### Post by sagar_aarya on 2012-05-24
> **fantab said:**
> Since you already formatted Ubuntu, tell us if you have a separate /home and did you format that too?

If you haven't then there could old XMMS2 configuration file present that are causing the problem... 
In that case, do have any valuable DATA on /home that you wish to preserve? 
If not, then I suggest you upgrade to Ubuntu 12.04 and format /home as well.

Nope i didnt formatted yet,

I came across this problem 3 months back also,At that time I formatted it.

---

### Post by sagar_aarya on 2012-05-24
??

SOmebody help mee...


:confused::confused::confused::confused:

---

### Post by fantab on 2012-05-24
You haven't answered the questions. 
Do you have a separate /home?
Is there any valuable data on the Hard Disk that you wish to save?

If Data loss is not an issue then I suggest you reinstall, preferably Ubuntu12.04.

You can also use [**CHROOT**]("https://help.ubuntu.com/community/BasicChroot") from your Ubuntu LiveCD and try to fix the problem by deleting the old XMMS2 files... ie, if you are sure that the problem is caused by said culprit. Remember, you will have to delete even the dot.files. 

 Read the link carefully and try... you can also use chroot to rescue or save any data.

Another LinK to set up [**chroot**]("http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation").

---

