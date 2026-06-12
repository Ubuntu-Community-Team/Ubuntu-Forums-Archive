---
title: "manually change what programs are started at login"
date: 2006-02-12
forum: General Help
---

### Post by harty83 on 2006-02-12
Howdy,

Is there a way to manually change what programs are started at login?  I know that if you shut down with the program running, it will automatically start back up when you log in next.  But here is my problem.  I recently set up a kolab server and I have kmail setup to connect to that server.  Before, kontact would be started with kmail inside it.  But now, with kmail set up to connect to my kolab server, it will startup separate from kontact for whatever reason.  I would like kontact to start up with kmail inside it, not kmail by itself.  Any clues on how to get this working?  Again, it only does this when I have kmail set up to connect to my kolab groupware server.

Thanks!

---

### Post by Rog131 on 2006-02-12
Maybe this helps ? 

Autostart Kubuntu package - [http://www.kde-apps.org/content/show.php?content=35038](http://www.kde-apps.org/content/show.php?content=35038)

Description:
Autostart is a KDE control center module for configuring which applications
start up when KDE inits (after a login).

---

### Post by harty83 on 2006-02-12
I installed the module and I actually like it better than the session manager.  I configured session manager to start with a blank session each time.  Then I set up autostart to start the specific programs I want.  I've tried kontact and without kontact, but kmail still starts at login.  

I've searched around and found that a couple others were having the same issue when they setup kontact to connect to a kolab server. But I couldn't find a solution.  There has to be something telling kde to start kmail.  But where??

---

### Post by bountonw on 2006-02-12
I am using Gnome, and also want to do things from the command line so that if I change distros in the future, I kind of know what is going on.  When I login, I get gaim and a terminal automatically.  I want to change that.  I also want a certain program *** to come on when my five year old son logs on and a different program when my wife logs on.  They each have a regular program that they use.

---

### Post by bountonw on 2006-02-14
I found out how to do what I want using the session manager in System>Preferences>Sessions the automatically save changes to session.  Open the programs that I want to open on boot click to automatically save in the session manager and then reboot.  Then go and remove the automatic option.  

Question:  Can this only be done from the gui?  Like I said, I am trying  to understand the command line so that I can be more functional between distros.

---

