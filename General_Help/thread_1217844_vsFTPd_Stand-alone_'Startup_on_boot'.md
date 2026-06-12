---
title: "vsFTPd Stand-alone 'Startup on boot'"
date: 2009-07-20
forum: General Help
---

### Post by HD Chang on 2009-07-20
Hello,

I have searched around for setting up vsFTPd to start on boot and I found that it can be configured through inetd where it is "run on demand" or as a "stand-alone" which is what I have installed.

Needless to say, I *REALLY* like the flexibility it gives me and I want to run it full time unless I stop it (unlike what i thought I would do, run it when I need it).

Problem is I am pretty new to linux and i'm not sure how to get it to run at startup.  It has to run sudo because it uses port 21 so I dont think it will work as a startup process [under my startup apps].

I have tried to start it a couple different ways from terminal:
sudo /etc/init.d/vsftpd start (Works great)
&
sudo vsftpd& (Works great)

I then ps aux | grep vsf
and it shows that its running under both (seemingly normally)

First: What is the point of the /etc/init.d script?  Is that just making it easier to start/restart/stop via a script rather than looking up a PID and killing it when you want to stop it? or restart it?

Second & Most Important: How do I translate this to run at startup?  Do I need to write my own script or something?  Can I just add it to a file somewhere (ie: /usr/sbin/vsftpd in rc.local) or something?

I am really clueless on where to begin.  If you could point me in the right direction I would appreciate it.

Thanks.
HDC

---

