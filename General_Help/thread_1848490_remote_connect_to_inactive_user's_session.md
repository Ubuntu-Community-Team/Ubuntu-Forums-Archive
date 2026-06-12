---
title: "remote connect to inactive user's session"
date: 2011-09-22
forum: General Help
---

### Post by supportagent11 on 2011-09-22
Suppose I have two ubuntu 11.04 machines, <Server> and <Laptop>.
The primary purpose of the <Server> machine is to run xbmc as a media center; its secondary purpose is to download torrents running transmission.

Ideally, I would like to create two user accounts on <Server> and switch between the two, so that the active login "user1" runs xbmc and the inactive login "user2" runs transmission.

Right now, I can only VNC into the active user's session... Is it possible to leave <Server> logged in as user1 (displaying xbmc on a television) and then remotely connect from <Laptop> to <Server> as user2 to use transmission without interfering with user1's xbmc session?

I had some success running tightvncserver and creating an alternate "user1" desktop to run transmission in, however I would prefer to keep the option of switching between users on <Server>.

---

### Post by supportagent11 on 2011-09-23
Alternatively, is it possible to VNC into user1's workspace2 without disturbing xbmc running in workspace1?

I was able to create a tightvncserver on port 5901 and open a vncviewer window in user1's workspace2 on <Server>, leaving xbmc undisturbed in workspace1... however I'd take any suggestions for setting up a dual-user environment like I outlined above.

---

