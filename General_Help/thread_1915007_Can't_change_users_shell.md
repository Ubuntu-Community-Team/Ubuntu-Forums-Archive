---
title: "Can't change users shell"
date: 2012-01-25
forum: General Help
---

### Post by warmnscsi on 2012-01-25
I have a user (bozo) set up on a test machine and when I try > chsh -s /bin/false bozo

I get: 

> chsh: "/bin/false" is not executable.


I checked the permissions on /bin/false and it is set as follows

> -rwxr-xr-x. 1 root root  24592 May 30  2011 false


Any ideas whythis doesn't work? I'm using CentOS 6.

---

### Post by gsgleason on 2012-01-25
> **warmnscsi said:**
> I have a user (bozo) set up on a test machine and when I try 

I get: 



I checked the permissions on /bin/false and it is set as follows



Any ideas whythis doesn't work? I'm using CentOS 6.

I find it odd that you're posting about a CentOS issue in the ubuntu forums.

Anyway, what if you just manually edit /etc/passwd, or use usermod -s?

---

### Post by warmnscsi on 2012-01-25
Thanks usermod -s did work. 

I've been on this forum for a while now so I usually just come here for all my linux questions but I guess I should stop being lazy and join a cent forum. So far everyone on this forum has been pretty awesome at answering all my questions.

---

