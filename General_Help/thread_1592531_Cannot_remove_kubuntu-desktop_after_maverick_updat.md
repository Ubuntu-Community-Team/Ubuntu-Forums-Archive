---
title: "Cannot remove kubuntu-desktop after maverick update"
date: 2010-10-10
forum: General Help
---

### Post by tarekeldeeb on 2010-10-10
Hello community,

Congrats for all of us! Happy new Ubuntu :)

I had ubuntu 10.04, with added kubuntu-desktop. Then I upgraded to 10.10 through 'upgrade-manager -d'

Now I need to fully remove kubuntu, but I cannot.

```
sudo apt-get remove --purge kubuntu-desktop
```
This only removes the dummy package. All KDE components still exist.

I tried [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome"), with no luck to return to pure gnome.

Can any one help? Is it a bug?

Thanks

---

### Post by NCLI on 2010-10-11
What happens when you try to use the puregnome command?

---

### Post by exit(1) on 2010-10-12
I had the exact problem with a fresh install of 10.10 which I installed kubuntu-desktop on.

I solved it by looking in /var/log/apt/history.log for the command that I used to install kubuntu-desktop.

It then shows everything the kubuntu-desktop pulled in as dependencies in a format like this:
```
kubuntu-debug-installer:amd64 (10.10ubuntu4, automatic), libkworkspace4:amd64 (4.5.1-0ubuntu8, automatic), libdbusmenu-qt2:amd64 (0.6.4-0ubuntu1, automatic), plasma-widget-kimpanel-backend-ibus:amd64 (4.5.1-0ubuntu4, automatic), libkresources4:amd64 (4.5.1-0ubuntu1, automatic), qapt-batch:amd64 (1.0.3-0ubuntu2, automatic), python-packagekit:amd64 (0.6.8-0ubuntu3, automatic), ksystemlog:amd64 (4.5.1-0ubuntu1), libprocesscore4a:amd64 (4.5.1-0ubuntu8, automatic), libpackagekit-qt-14:amd64 (0.6.8-0ubuntu3, automatic), libkldap4:amd64 (4.5.1-0ubuntu1, automatic), kde-zeroconf:amd64 (4.5.1-0ubuntu2), kppp:amd64 (4.5.1-0ubuntu2), libktnef4:amd64 (4.5.1-0ubuntu1, automatic)
```

I used a couple sed commands and a python script to take out all the unneeded information.
Then I did: ```
sudo apt-get autoremove --purge <list of packages>
```

Make sure it doesn't take out anything your system needs...
I realize my situation isn't the exact same as yours but hopefully this will help.

EDIT: Expanded on format of history.log

---

### Post by HermanAB on 2010-10-12
Howdy,

You want to unscramble an egg?

If you have a separate /home directory, re-install and don't format /home.  Otherwise, fuhgeddaboudit.

---

### Post by angryfirelord on 2010-10-14
In the past, I used apt-get autoremove to remove a package's list of dependencies. I think this was integrated into later versions of apt, but I'm not sure. It's worth a try though.

---

