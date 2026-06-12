---
title: "Help with sound - multiusers"
date: 2011-06-30
forum: General Help
---

### Post by oyinbo55 on 2011-06-30
I hope I am posting my question correctly:
I also need to logout a user without the session-save command.  We have two users on the same machine.  However, user2 somehow disrupts the use of sound services for user1.  I don't know which process is causing the problem.  We need to shut off user2 and close all processes without saving the session.  As Cokedude mentioned, logout/exit only closes the terminal session.  Oddly, even after rebooting the machine, user2 still appears on the login screen as logged in.  I can only imagine the kind of baggage the system will have when we have ten or more users occasionally using this machine.  Is there a functional logout command?

---

### Post by bodhi.zazen on 2011-06-30
I moved your thread , please do not post a new question on a 7 month old, unrelated topic.

I also gave your post a more appropriate title.

Something seems amiss with your system as the behavior you describe is not normal.

First there is the issue of a user showing as logged in at boot - not normal.

Second, when switching users, (I have 4 children) we do not have this problem.

I would look at what commands, if any, you are running at boot or custom commands you are running with the problematic user or pulseaudio.

---

