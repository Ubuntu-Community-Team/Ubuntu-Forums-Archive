---
title: "FreeNX multiuser question"
date: 2006-06-06
forum: General Help
---

### Post by flusteredpie on 2006-06-06
Hi there,

I've recently purchased a second more powerful system which is seated at one end of my room. My older computer, a laptop, is set up beside my bed. I'm currently using FreeNX to login to the newer system from my laptop, and start a new gnome session.

What I want to be able to do, is to open a media file on the laptop session (using totem), and have totem actually open on the newer systems session. Essentially, i'm looking to use the laptop as a remote control :P Is this possible? Idealy, i'm looking to do this via a console window.

Hope what I've said makes sense to someone.

All suggestions appreciated

Neil

---

### Post by flusteredpie on 2006-06-06
Oh, just for the record, this question is in no way totem specific. What I'm really asking is is it possible to run ANY command as one user, and have it run on another users session.

Thanks in advance
Neil

---

### Post by rvergara on 2006-06-10
Short answer is no. 

This is one of the fundamental reasons why Linux is safer than windows. You can not run commands as a different user (unless you have specifically received these privileges).

Long answer is I think you can do what you can.

Use your laptop to run the same user as your new system (yes, you can have 2 sessions with the same user). There are some programs that we do not allow 2 instances in different X servers however some programs will.

In your freenx client in the laptop, do not allow media programs to be shared remotely and then connect your freenx client in your laptop. Try to run modem and I believe the program will run in your newer system.

A caveat. I have not tested here.

Please report your results since it is an interesting question.

Regards

Ramiro

---

