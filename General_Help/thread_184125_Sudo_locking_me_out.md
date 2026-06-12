---
title: "Sudo locking me out?"
date: 2006-05-29
forum: General Help
---

### Post by Ray100 on 2006-05-29
I was having problems with install 5.10 that seemed to be related to sudo not passing along information to the required programs. I was able to start the program from the command line but not from the graphical menu.
I decided to update to version 6 hoping that whatever it was would fix itself.

If I try and run network-admin it asks me for my password, which I give, the a box pops up saying

"Failed to run network-admin"
"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator"

Problem being the sys-admin, me, hasn't a clue :-? 

Here's the previous post I made where kingmonkey was kind enough to try and help me

[http://www.ubuntuforums.org/showthread.php?t=183161](http://www.ubuntuforums.org/showthread.php?t=183161)

I don't know if the problems are related, it seems that they might be, both havind to do with sudo.

Can anyone help with this?

Ray

---

### Post by adwait on 2006-05-29
Are you the first user created on the system? Are you allowed to use sudo?

---

### Post by Ray100 on 2006-05-29
Yes, I'm the only user.

---

### Post by steve.horsley on 2006-05-29
What happens when you try and run **sudo id**? I'm really interested in any error message. If it actually works and tells you that you are root, then you can always run **sudo network-admin**. If you get an error, the message may help diagnose the problem.

---

### Post by Ray100 on 2006-05-29
If I run sudo id, nothing happens. I can run id as root and get uid=0(root) gid=0(root) groups=0(root)

---

### Post by steve.horsley on 2006-05-31
You just get the command prompt back, with no output? 
I'm sorry, I can't imagine what that might be caused by.

---

