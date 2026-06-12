---
title: "Login Issue"
date: 2011-03-10
forum: General Help
---

### Post by Seeked on 2011-03-10
I am running Ubuntu 10.10 on a Lenovo Z61m and have been doing so without issue for some time.  

I am having a funky issue at login.  When I enter my username/password at login with the GUI (I disabled the list of users some time ago) the screen will flicker then return me to the login screen.  There is no notification of an error.  It doesn't matter if I try the recovery console or safe mode there is the same issue when I try and login with this user.  

However,  I can login with a different user open a console and su to that user that wouldn't login at the GUI.

Any thoughts, ideas or suggestion?

Thank you for your time.

---

### Post by bodhi.zazen on 2011-03-10
Hard to know. Check your logs. My guess is you have a corrupt configuration file in your home directory.

You can try booting to single user mode and as root:

mv /home/your_user /home/old_home
mkdir /home/your_user
chown your_user:your_user /home/user

Then reboot and you should be able to log in. Any old data will be in old_home.

---

### Post by Seeked on 2011-03-11
I tried deleting all of the directories in my home directory that might contain any gnome settings.  I was getting desperate so I installed KDE to try and get in so I could have an easier time backing things up (such as evolution) before reinstalling Ubuntu but the SAME thing is happening when I try to login with KDE, any ideas?

---

### Post by mssever on 2011-03-11
This probably has nothing to do with Gnome or KDE; those start up later in the login process. Look in ~/.Xsession-errors and other relevant dotfiles for some hints. Also, check your home directory's permissions.

Finally, you can try bodhi.zazen's suggestion. It'll reset whatever went screwy.

---

