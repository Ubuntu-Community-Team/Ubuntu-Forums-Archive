---
title: "broken packages!!"
date: 2009-10-05
forum: General Help
---

### Post by mickmouse13 on 2009-10-05
I know this problem has been posted before but in all the other threads i did not find what i need. i used the add/remove utility to try and download funguloids something happened and i stopped the download. now i cant download it fully i get this when i try a window pops up that says 

"AN UNKNOWN ERROR UCURED
this should not happen"
and than it has this output
"Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 91, in _process_transaction
    self.install_packages(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 155, in install_packages
    self._mark_packages_for_installation(package_names)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 197, in _mark_packages_for_installation
    pkg.markInstall()
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 1076, in markInstall
    fixer.Resolve(True)
SystemError: E:Unable to correct problems, you have held broken packages.
"
im running 9.10beta and other thigns install okay i think. if anyone knows how to fix it please post.

---

### Post by FrostDust on 2009-10-05
Open a terminal and try running:

```
sudo dpkg --configure -a
```

---

### Post by mickmouse13 on 2009-10-05
I used that command and it went through alright. there was no output in the terminal. i went to add/remove to try again and it did not mess up right away it asked me to authenticate by pushing a button. i did and it just kinda sat there, after a while it said it lost connection to daemon and closed. so i went to try it in the package manager. it said i needed other packages so i clicked to select them all then a windows saying 
"COULD NOT MARK ALL PACKAGES FOR INSTALLATION OR UPGRADE
the following packages have unresolvable dependencies.
make sure that all required repositories are added and enabled in the preferences." 
with this output
"funguloids:
 Depends: ogre-plugins-cgprogrammanager  but it is not installable"
i will work on finding ogre but if anyone knows anything else please post =)

---

### Post by FrostDust on 2009-10-05
"dpkg --configure a" simply fixes your list of installed packages in case it gets messed up, such as an install procedure getting interrupted.

In your case, it seems like your package is not included in the repositories [for some reason]("https://bugs.launchpad.net/ubuntu/+source/funguloids/+bug/194686").


Try [going here]("http://packages.debian.org/sid/ogre-plugins-cgprogrammanager"), and go to the bottom of the page to download the file you need.

---

### Post by mickmouse13 on 2009-10-05
got it downloaded. i went to a site and got the package containing "ogre-plugin-programmanagar" or what ever.  the problem was just that my system could not connect to the right sites maybe? anyway thanks for your helps. the game still does not work, it "unexplainable crashes" when i open it. oh well.

---

### Post by mickmouse13 on 2009-10-05
this is what i did. it got me able to download everything. but the game crashes on open.

---

