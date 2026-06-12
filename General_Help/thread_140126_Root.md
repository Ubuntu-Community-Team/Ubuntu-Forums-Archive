---
title: "Root"
date: 2006-03-05
forum: General Help
---

### Post by Mr X on 2006-03-05
I really need to log into root in Kubuntu. How do I do this?

---

### Post by ren wins on 2006-03-05
sudo?

---

### Post by Mr X on 2006-03-05
Is there anything else I need to know?

---

### Post by Mr X on 2006-03-05
I tried sudo as a username, and I tried the password I used to setup my first kubuntu account. It says login failed. Why?

---

### Post by ren wins on 2006-03-05
i'm sorry i wasn't more clear.  I kind of hate when people tell me to do obvious things when i try to solve a problem, but that's my problem ;).

why do you need to log in as root? are you new to ubuntu/debian?
you would use sudo in a terminal window to preface a command you want to run  as root.  I dint know how to log into kubuntu as root, but i suspect you would have to make a completely new log-in and give it root privilages for everything... but most people seem to think that that is a HORRIBLE idea, and i'll agree with them (though i'm not entirely clear why)

---

### Post by lupine_nickt on 2006-03-05
People make a big fuss about logging in with root, but sometimes it makes life a lot easier :). Here's how:

1. Open up a normal terminal
2. 'sudo passwd'

You'll be prompted 'Password:' - enter your normal Sudo password. Then you'll be prompted 'Enter new UNIX password:' and (once you've done that) 'Retype new UNIX password:' - that's for your root password. From there, you should be able to log into terminals and KDE as root... obviously, your ~ will be /root and Desktop will be ~/Desktop

You also have to be careful with file permissions - especially when messing around in your normal user's home folder. As root, 'chown -R <username> /home/<username>', where <username> is your normal login, will sort out your problems if you make changes, login as your normal user, then keep getting 'access denied'.

Of course, as root, it is dead-simple to kill your entire system. F'rinstance, 'rm -rf /' is something you *never*, ever want to type ;)

HTH...

xF,

...Nick

---

### Post by aysiu on 2006-03-05
Explain *what* you're trying to accomplish, not *how* you're trying to accomplish it, and I'll explain to you how to do it without logging in as root, and I can almost guarantee my way (which is the default in Ubuntu) is easier and faster.

---

