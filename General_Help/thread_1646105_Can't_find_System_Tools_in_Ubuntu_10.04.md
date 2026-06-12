---
title: "Can't find System Tools in Ubuntu 10.04"
date: 2010-12-15
forum: General Help
---

### Post by markcoronado on 2010-12-15
I just installed Ubuntu Tweak & I can't find how to access it.
I read that it is under Applications - System Tools- Tweak
My problem is when I click Applications the only items that are there is 
Accessories
Games
Graphics
Internet
Office
Sound & Video
Ubuntu Software Center

There is no System Tools.
How do I find it?

---

### Post by TeoBigusGeekus on 2010-12-15
Right click the menus>Edit menus>Check system tools.

---

### Post by markcoronado on 2010-12-15
> **TeoBigusGeekus said:**
> Right click the menus>Edit menus>Check system tools.

Every time I check the system tools box within less than 3 seconds the check mark disappears.

I tried it about 10 times & even rebooted & tried it again with the same results.

Any suggestion on how to get the check mark to stay?

---

### Post by Krytarik on 2010-12-15
Is there at least an entry for Ubuntu Tweak in the submenu-list of "System Tools" in the menu-editor? If so, is it checked. If there is no single item checked in a submenu, it will not be activated.

---

### Post by markcoronado on 2010-12-15
> **Krytarik said:**
> Is there at least an entry for Ubuntu Tweak in the submenu-list of "System Tools" in the menu-editor? If so, is it checked. If there is no single item checked in a submenu, it will not be activated.

OK here is what I did.

Right click on Applications
Left click Edit Menus
Left click System Tools under Menus:
On the right pane under Show Items there is no Ubuntu Tweak & none of the other items are checked so I put a check in the File Browser box & now System Tools is checked & it now shows when I click on Applications.
Still no Ubuntu Tweak.
If I go to the software center I can't find Tweak under installed software but if I go to Get Software- Tweak is showing the Remove box & a green check mark next to Installed.
Now what?

---

### Post by Krytarik on 2010-12-15
How did you install it in the first place, via "Ubuntu Software Center"?

If so, remove it via USC and install it this way, in a terminal:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

---

### Post by markcoronado on 2010-12-15
> **Krytarik said:**
> How did you install it in the first place, via "Ubuntu Software Center"?

If so, remove it via USC and install it this way, in a terminal:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Well I found out that the tweak that I installed via USC wasn't the same as Unbuntu Tweak.
I did a google search for Unbuntu Tweak & found it on the ubuntu-tweak web site so I downloaded version 0.5.7 & installed it & now it shows under System Tools.

I hope it was ok to install it that way & not the way that you described?
If not let me know please.

---

### Post by Krytarik on 2010-12-15
As I've posted in another thread:

Nowadays many third party developers make their packages available via ppas AND deb-packages. If available I would always chose to install them via ppa, because they will be updated automatically if a new version becomes available.

---

### Post by markcoronado on 2010-12-15
> **Krytarik said:**
> As I've posted in another thread:

Nowadays many third party developers make their packages available via ppas AND deb-packages. If available I would always chose to install them via ppa, because they will be updated automatically if a new version becomes available.

Should I uninstall it & reinstall via ppas?

---

### Post by Krytarik on 2010-12-15
> **markcoronado said:**
> Should I uninstall it & reinstall via ppas?
Short answer: Yes.;)

EDIT:
```
sudo apt-get remove --purge ubuntu-tweak
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

---

### Post by markcoronado on 2010-12-15
> **Krytarik said:**
> Short answer: Yes.;)

EDIT:
```
sudo apt-get remove --purge ubuntu-tweak
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```


I ran that code in terminal & it removed it but I don't think it installed it because it no longer shows when I click on system tools.

Here are the results.
mark@mark-laptop:~$ sudo apt-get remove --purge ubuntu-tweak
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 nspluginwrapper libswfdec-0.8-0 ia32-libs
  libc6-i386 lib32gcc1 lib32asound2 lib32z1 lib32stdc++6 lib32v4l-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntu-tweak*
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
After this operation, 3,916kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 149343 files and directories currently installed.)
Removing ubuntu-tweak ...
Purging configuration files for ubuntu-tweak ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
mark@mark-laptop:~$

---

### Post by Krytarik on 2010-12-15
What about the other commands?
Enter all of them, after each other.#-o

---

### Post by markcoronado on 2010-12-15
> **Krytarik said:**
> What about the other commands?
Enter all of them, after each other.#-o

OK I got it now.
I C&P all 4 at once, I see now that it doesn't work that way.
Thanks for all the help.
I'm new to Linux & I guess it will take awhile to get used to it.
Thanks again.

---

### Post by Krytarik on 2010-12-15
So, if you're about to tweak your system a little bit, this one is even not included in Ubuntu Tweak, I just discovered it in the last days:
[http://ubuntuforums.org/showthread.php?p=10225467#post10225467](http://ubuntuforums.org/showthread.php?p=10225467#post10225467)

Happy Ubuntu'ing!

PS: Please mark this thread as "solved", via "Thread Tools", I guess.

---

