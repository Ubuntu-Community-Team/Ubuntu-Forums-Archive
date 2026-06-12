---
title: "Wrong credentials for GUI"
date: 2012-10-11
forum: General Help
---

### Post by niranjan_rao on 2012-10-11
I think this is a bug, but wanted to confirm here first.

I have two accounts on machine - first one was created when I built the machine and is part of sudo group.

Other account is coming from active directory, this account also has admin permissions - that is it can execute commands using sudo. This is my normal work account and I do execute sudo commands all the times from terminal.

However if I run some GUI application that needs sudo permissions - e.g. ubuntu software center application to install new software, my active directroy password does not work. It just asks me the password, but password it needs seems be that of default login and not active directory login. I have noticed same thing happening with other GUI applications that need authentication aslo.

Is there possibility that GUI sudo authentication and terminal authuntication are following different pahs? Terminal sudo authentication does work as expected if I enter my active directory password.

---

### Post by ajgreeny on 2012-10-11
Forgive me if you are aware of this, but GUI applications do not, or should not, use sudo.  They use **gksu** or **gksudo** in gnome or other gtk DEs such as Xubuntu and Lubuntu, and **kdesu** in KDE or other QT DEs, eg razor-qt.

---

### Post by critin on 2012-10-11
>  but password it needs seems be that of default login

Yes.
Software, etc needs the login password for the user that logged in for that session.  You do know that you do not add 'sudo' to those types of  authentication?  Just the password.

---

### Post by niranjan_rao on 2012-10-12
I see I created some confusion in terminology. What I meant was when the program needs to elevate the previlages whether from terminal or from UI.

Here is example of what I mean.

From terminal prompt if I type the command 

sudo apt-get install <some package I need>

This asks me for the password. The password I enter is for my current login. And this works.


Now if I go to ubuntu software center and try to install something I want, it asks me for the password. If I enter my current password here (which worked on above case), it does NOT work. I have to enter password for the default login. 

So the question is why does terminal pervilage elevation accept my password and GUI based applications do not

---

