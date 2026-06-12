---
title: "Software center hangs"
date: 2012-09-30
forum: General Help
---

### Post by Nico-dk on 2012-09-30
This problem started today.
Whenever I start software Center, a white windows pops-up and after a few seconds it hangs (turns gray), and has to be forced closed.

Starting from terminal:
```
softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
```

Earlier this morning it was working just fine
The only changes I've made today is installing openra from a .deb (it has later been removed). Prior to the problem, I tried installing playonlinux using the latest ubuntu .deb package from [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Things I've tried:
```
sudo apt-get remove software-center
sudo apt-get remove software-center
```
```
sudo apt-get install --reinstall software-center
```
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```
```
sudo apt-get --purge remove software-center
```
```
sudo aptitude reinstall software-center
```

I'm running Ubuntu 12.04

---

### Post by Nico-dk on 2012-10-01
Thinking it was something to do with a ""corrupt" .deb package, I tried

```
sudo apt-get clean
sudo apt-get autoremove
```

This didn't remedy the problem.

Could this be a permission problem?
Like something in my home dir has changed from my user to root?

After work, I'll try

```
sudo software-center
```


Suggestions, feedback or any useful input would be greatly appreciated

---

### Post by Nico-dk on 2012-10-01
So it seems the problem is permission related, since SC starts up when using sudo from terminal.

Terminal output after sudo software-center

```
2012-10-01 15:55:21,060 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-01 15:55:21,067 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-01 15:55:21,439 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-01 15:55:21,603 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-10-01 15:55:21,606 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-10-01 15:55:24,430 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2012-10-01 15:55:28,614 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-10-01 15:55:28,615 - softwarecenter.db.database - INFO - reopen() database
2012-10-01 15:55:28,615 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-01 15:55:34,865 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
```

Suggestions, fixes etc. are still more than welcome

---

### Post by GreatDanton on 2012-10-01
Try gksudo software-center. Gksudo is used for graphical apps, while sudo is not.

Regards.

---

### Post by jerrrys on 2012-10-01
I have not encountered this problem, but just maybe you can find an answer [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=glib+Error&as_qdr=all&sa=Google+Search&lang=en")

good luck

edit:  got a better hit [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=software+center+glib+Error&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by Nico-dk on 2012-10-01
Thanks, and yes this works as well.

I'm just a bit baffled, that I suddenly need to start SC as root. I know SC actions (and most of not all related files) requires root to use, but howcome I suddenly need to sudo to get it to run?

```
me@G555:~$ cd /etc/apt/
me@G555:/etc/apt$ ls -l
total 68
drwxr-xr-x 2 root root  4096 Sep 28 09:36 apt.conf.d
-rw-r----- 1 root root   130 May 12 15:13 auth.conf
drwxr-xr-x 2 root root  4096 Apr 20 12:21 preferences.d
-rw-r--r-- 1 root root  2941 Sep 30 15:40 sources.list
drwxr-xr-x 2 root root  4096 Oct  1 16:06 sources.list.d
-rw-r--r-- 1 root root  2941 Sep 30 15:40 sources.list.save
-rw------- 1 root root  1200 Sep 30 08:29 trustdb.gpg
-rw-r--r-- 1 root root 16923 Sep 30 16:07 trusted.gpg
-rw-r--r-- 1 root root 16321 Sep 30 08:29 trusted.gpg~
drwxr-xr-x 2 root root  4096 Apr 20 12:21 trusted.gpg.d
```

*edit*
Thanks jerrys.
I've been hunting this so far

```
softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
```

---

### Post by Nico-dk on 2012-10-02
Problem still persists, but I'll just leave it for now, and open software center from terminal with

```
sudo software-center
```

---

