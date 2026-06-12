---
title: "Unable to log in with a certain user but can log in with a different user"
date: 2012-09-01
forum: General Help
---

### Post by Headfirst on 2012-09-01
I have a desktop I'm in the process of configuring to be a home media server ( setting up Samba and Media tomb for starters) I powered down the computer a couple days ago. Today when I turn it on it boots up just fine to the Ubuntu 12.04 login screen where I can select either UserA or UserB. When attempting to log in with UserA after I put in the password and hit enter the screen goes black briefly as if it is loading the desktop, but then it just goes back to the Login Screen. If I type in the wrong password it does tell me the password is incorrect so I know that's not the issue. If I log in with UserB which I hardly ever use I am able to log in just fine and the desktop loads so I'm wondering if this is some sort of corrupt user file or what? I've been using Ubuntu for quite sometime, but I've not encountered this particular issue before.

I'm using a 32-bit install of version 12.04 and I used Ubuntu 2D.

Any suggestions would be greatly appreciated!

---

### Post by ryanyeah on 2012-09-01
Login with the working user or root and try to su to the other user and see if that works? If it does, try resetting the other user's passwd and then trying to log in.

---

### Post by steeldriver on 2012-09-01
You could try logging in to one of the virtual terminals (Ctrl-Alt-F1 etc.) - if that works it means there's nothing wrong with your account / password, just a problem starting your graphical X session - if that's successful, then check the ownership / permissions of your session authority files

```
ls -l ~/.{ICE,X}authority

```
If they aren't owned and rw by you then

```
rm ~/.{ICE,X}authority
```

and try again at the graphical greeter (Ctrl-Alt-F7 to get back there from the VT)

---

### Post by Tobeus on 2012-09-01
You also might check out what is in /var/log/auth.log and see if there is anything interesting in there.  There are several log files that can help you figure out what the problem is in the /var/log directory.

Other than that, I would agree that switching to another terminal and logging in to the command line would be a good way to find out (Ctrl+Alt+F1).  Use Ctrl+Alt+F7 if you need to return to the GUI interface.

Hope that helps!

-Tobeus

---

