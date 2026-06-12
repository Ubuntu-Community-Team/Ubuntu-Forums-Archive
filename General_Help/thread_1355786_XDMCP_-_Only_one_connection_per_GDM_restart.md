---
title: "XDMCP - Only one connection per GDM restart"
date: 2009-12-15
forum: General Help
---

### Post by gary.lundie on 2009-12-15
Hi All,
 
I'm trying to setup an Ubuntu 9.10 box that I can use XDMCP to remote into.  I have enabled XDMCP, and can connect to it using XManager.  However, the issue I'm having is that I can connect and login fine, but when I logout, I cannot reconnect to XDMCP until I restart GDM.
 
Theres nothing in /var/log/auth.log that would indicate any issues.
 
I'm currently running XManager on a Windows 7 PC, however, when I try the same scenario on another maching running XP, I have no issues, everything works as expected.
 
Any ideas what would cause this?
 
Also, just as a quick aside, could someone tell me the ports I need to open on my router to allow XDMCP connection remotely?
 
Thanks in advance,
Gary

---

### Post by stanfordcg on 2010-01-12
Getting the same, log in using Xming then Logout, next time i try to login using Xming i get a flash of screen then nothing. Restart GDM and I can log in again from Xming.
 
Worked fine in 8.10 and 9.04, stopped after upgrading to 9.10
 
Any luck in finding a solution?

---

### Post by vbuffern on 2010-01-13
I have exactly the same issue than [stanfordcg]("http://ohioloco.ubuntuforums.org/member.php?u=996443"). 
I have configured XDMCP on Ubunutu 9.10. The first connection is successful. Then, if I logout and try to login again, I get the login prompt but I cannot open a session.

I have tried to use KillInitClients=true and DisplaysPerHost=2 without success.

I have notice that I have some pulseaudio processes running. 
If I kill them and try to login again, I randomly succeed.

My XDMCP client is XMing. 
My XDMCP configuration works fine with a previous Ubuntu version.

Any idea ?

---

### Post by mandhyl on 2010-01-14
Me too, I have the same problem whith XMing...

What can we do ?



All right, read this: [http://www.peppertop.com/blog/?p=671](http://www.peppertop.com/blog/?p=671)

---

### Post by lilaboc on 2010-01-20
Hi, I'm on ubuntu 9.10, and I met the same problem as yours. But after I added one line "DisplaysPerHost=2" in /etc/gdm/custom.conf, the problem was gone.

---

