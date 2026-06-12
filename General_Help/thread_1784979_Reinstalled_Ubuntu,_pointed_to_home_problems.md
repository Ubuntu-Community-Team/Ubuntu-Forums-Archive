---
title: "Reinstalled Ubuntu, pointed to /home problems"
date: 2011-06-17
forum: General Help
---

### Post by polardude1983 on 2011-06-17
Using ubuntu 10.04.2 and reinstalled ubuntu 10.04.2

Ok so my ubuntu was doing fine but then i was having an error and ubuntu was no longer loading

My ubuntu installation is on sda1 and my /home was on sdb3

So I inserted the live cd and hit reinstall and pointed the / to sda 1 and to format it and to point /home

I told it to format sda1 where its installing / to and told it not to format sdb3 for /home

So i restarted my pc and well none of my applications that are installed on the /home dir are recognized by the system and most of them aren't in the gnome applications menu.

The only applications that are in the applications menu  are skype, teamviewer and a wine program but when i try to load them it for example skype it says no skype folder. also my chrome browser isn't installed either.

anyways help would be appreciated

---

### Post by ruffEdgz on 2011-06-17
Even though you have .<application> folders in your home directory doesn't mean that the programs you want to use will be there. Usually, the .chrome, .firefox, .skype, etc... are mostly there for configuration purposes. You will probably have to install the applications again using a terminal or the "Ubuntu Software Center".

If you didn't download those applications using the Ubuntu repo but had them in a folder in your home dir, then you can make a new desktop icon (right click on the desktop, select "Create Launcher"), move or copy that file into /usr/share/applications/ which is kind of hackish but it works :P

Also, the apps you see in the applications menu, are they pointing to the correct location when they are trying to execute?

---

### Post by mikewhatever on 2011-06-17
You need to reinstall all 'your' applications, as none of the mentioned (and probably none of unmentioned) is located inside /home. /home only holds user configuration files.

---

### Post by polardude1983 on 2011-06-17
So what can i do to avoid this later? what folder does need to be backed up?

Also what about any repositories are those kept in the home folder or do i have to add those again?

---

### Post by mikewhatever on 2011-06-17
You can backup all of root, or just backup the list of installed packages and then use it to reinstall everything on the new installation.
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
The list of the default repositories is in /etc/apt/sources.list, and third party lists are ofter in /etc/apt/sources.list.d.

---

