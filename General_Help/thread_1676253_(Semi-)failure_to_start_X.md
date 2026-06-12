---
title: "(Semi-)failure to start X"
date: 2011-01-26
forum: General Help
---

### Post by anntzer on 2011-01-26
Hi all,
I have run into a problem some time ago, I had found a workaround but still I'd like to solve it properly as it's quite a pain.
So I'm running Kubuntu 10.10, and am unable to login graphically.  More precisely, after I enter my login and password, the screen goes partially black and then comes back to the login prompt.  The workaround I've found is to drop to the console, login and startx, which works fine.  Still, that creates problems (e.g. having to shut down the computer through sudo shutdown -P now) so a better solution would be appreciated.
I've already tried a few things mentioned on the forum: make sure that everything in /home/user is owner by user, delete .Xauthority, delete .ICEauthority, sudo service kdm start and login (fails the same way).  Even deleting .kde didn't work.
After the failed login, my .xsession-errors contains:

Xsession: X session started for user at mercredi 26 janvier 2011, 18:48:45 (UTC-0800)
QMetaObject::invokeMethod: No such method Konsole::Application::loadCommandLineOptionsForNewInstance()
x-terminal-emulator: Fatal IO error: client killed
konsole(2441) Konsole::SessionManager::~SessionManager: Konsole SessionManager destroyed with sessions still alive 

Also, it may be worth mentioning that trying to login (graphically) from a brand new account does work.
On a perhaps related point, when I drop to the console, every so often (with no apparent regularity) the screen just goes completely black, but the console is still there as I can still start KDE by entering my username, my password and startx (nothing at all appears on the screen while I type this, but KDE still starts properly after this).
Does someone has an idea to help me?
Thanks in advance,
Antony

---

### Post by Memento on 2011-01-27
It also happened to me when i upgraded to kde sc 4.6: kdm (or gdm) did not have a kde plasma entry so it looped like that.
I solved it by reinstalling kubuntu-desktop
have a look here [http://ubuntuforums.org/showthread.php?t=1675894](http://ubuntuforums.org/showthread.php?t=1675894)

---

### Post by anntzer on 2011-01-28
Thanks for your reply, but this doesn't seem to work for me...
Any other good ideas floating around?

---

