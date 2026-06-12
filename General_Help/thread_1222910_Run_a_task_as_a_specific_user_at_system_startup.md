---
title: "Run a task as a specific user at system startup"
date: 2009-07-25
forum: General Help
---

### Post by taelatus on 2009-07-25
Greetings.

I've been searching around for some information and have resorted to these boards for some assistance.  First, here's a brief description of what I'm doing.  I have setup, on an 8.04 desktop machine, a Source engine based server (Left 4 Dead).  I also have openssh-server installed so I can connect remotely into a terminal to start/stop the server.  It works great except for one thing: when/if the openssh connection times out, the server goes down.

What I would like to have is the server get started at system startup so it runs continuously.  Also, I would like the server to get started under a particular user.  What would also be nice is when I choose to login with ssh, I can see the server console.

I don't have access to the GUI so any interface tools are out of the question.  I took a look at cron but it doesn't seem to fit my purpose unless I wanted to stop/restart the server once per day.  Even then, I didn't see an option for starting the server as a particular user.  I know that you can use the interface Sessions menu to add things to a user startup, but that requires the user to be logged in.

Can anyone help me figure this out?  I'll be most appreciative.

---

### Post by taelatus on 2009-07-25
Bump.

---

