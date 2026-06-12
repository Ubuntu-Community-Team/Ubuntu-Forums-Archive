---
title: "Help, No login window option in my version of ubuntu-  v9.10"
date: 2010-01-18
forum: General Help
---

### Post by hurstw1 on 2010-01-18
I am tring to install Mac4Lin and I get to the step to go in and modify the login window and it does not appear as an option under system admin.  can anyone tell me why not?

---

### Post by VCoolio on 2010-01-18
Karmic (= ubuntu 9.10) uses a new but for the time being far less configurable gdm, which is the app that rules your login window. There are however ways to configure it; use the 'search forum' feature for a combination of karmic and gdm and you'll find a list of threads covering the issue.

---

### Post by growlf on 2010-01-19
Very correct.  Here are a couple things to help you...

The top active (with solutions) thread on this atm is [here]("http://ubuntuforums.org/showpost.php?p=8707543&postcount=55").

And a good app that fills in the missing gap somewhat is [here]("https://launchpad.net/gdm2setup").  This app is still in its infancy and does not have theme-file support _YET_, but it will and it does allow many of the old options again already.

[UPDATE] There is an installer for it now as well as a PPA (with instructions) for automatic updates to the tool.  Xsplash support is now the next goal for the project.

---

