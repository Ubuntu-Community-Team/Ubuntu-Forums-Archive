---
title: "vncserver crash on program start"
date: 2010-02-21
forum: General Help
---

### Post by kimyoungil on 2010-02-21
Hi all,

I've got the following problem with vncservers. This is the setup:
I've got a desktop running ubuntu for normal use.
I've got a small jornada 690 palmtop, with which I want to remotely connect to my desktop

I've made a new user account (mobile) on my desktop. Via ssh I connect to mobile@desktop, and start a vncserver (at low resolution). Then I can connect with tightvncviewer to the just started  vncserver on my desktop.


The vncserver works and i do get a desktop and stuff. however there are quite a lot of programs which crash the vncserver. For example programs which use the soundcard. But also things like evince (document viewer). It crashes so often that it becomes really useless. Just simple internet and nautilus mostly work, but almost everything else fails.

Connecting to my normal desktop is no option, because then I've got to look at a 1600x1200 screen on a 640x240 screen. 


What's going wrong here?

Can it be a problem that when programs start using specific hardware which is already in use on my normal desktop, that it crashes? vncserver logs don't tell anything interesting. Are there other logs to look at?

Should I file a bug report?

---

