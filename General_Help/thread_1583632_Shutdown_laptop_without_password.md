---
title: "Shutdown laptop without password"
date: 2010-09-28
forum: General Help
---

### Post by Harix on 2010-09-28
When running Jaunty, I could press the power button and my laptop turned off.
Now in Karmic, I am all the time asked to provide my password when shutting down.
I am the only user.
Can this be changed?
Thanks!

---

### Post by linux-hack on 2010-09-28
you can change settings in the power configuration.

---

### Post by Harix on 2010-09-28
Thanks Linux Hack, but there is nothing concerning password in my power configuration....(gnome-power-manager 2.28.1)
It is set on:  When power button is pressed: Shutdown

When I press the power button to shut down, I must enter my password, and I want to get rid of that...

---

### Post by linux-hack on 2010-09-28
Try changing your sudoers file like this :

```
sudo visudo
```

add a line like this :
```
USERNAME ALL = NOPASSWD: /sbin/shutdown
```

Or

If you want to put your group :

```
%GROUPE_NAME ALL = NOPASSWD: /sbin/shutdown
```

May be this will helps !!!

---

### Post by linux-hack on 2010-09-29
Did you resolve your problem ?

---

### Post by Harix on 2010-10-01
No, not yet.
I added yr proposed line, no results.
Now I cannot get into my sudoers file anymore....
I get:

hans@hans-laptop:~$ sudo visudo
[sudo] password for hans: 
hans is not in the sudoers file.  This incident will be reported.
hans@hans-laptop:~$ 

What to do next?

Thanks!

---

### Post by linux-hack on 2010-10-03
change the file with a live CD and add you user name.. What did you added to the file exactly ?

---

### Post by Harix on 2010-10-04
In the password screen I found a non working link:
Details: org.freedesktop.consolekit.system.stop-multiple-users

I googled this and  came to: (read the last 4 posts..)

[http://ubuntuforums.org/showthread.php?t=1328592&page=2](http://ubuntuforums.org/showthread.php?t=1328592&page=2)

I removed MythTV and now Karmic shuts down without asking for my password...

Thanks a lot for all yr advises!

---

