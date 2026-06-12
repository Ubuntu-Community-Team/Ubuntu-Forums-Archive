---
title: "ubuntu software center not opening in normal user mode in 12.04"
date: 2012-10-10
forum: General Help
---

### Post by xlearner on 2012-10-10
Hello All,

This query is regarding ubuntu software center. I am running Ubuntu 12.04. 

When I try to open it as a normal user it is not opening. For some reason it is getting stuck. But when I open it in super user mode it opens normally. It works when I open a terminal and type:

> sudo software-center

So can someone suggest what could the problem be and how to fix it?

Thanks
Xlearner

---

### Post by jerrrys on 2012-10-10
Quite a few post on it and a few marked solved.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=software+center+not+opening+12.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=software+center+not+opening+12.04&as_qdr=all&sa=Google+Search&lang=en)

Instead of sudo just do software-center in terminal to see what kind of errors you get.

---

### Post by xlearner on 2012-10-11
Dear Jerrys,

Thanks a lot for the reply. I searched in the link that you sent me. But somehow, I am not able to find a solution to my problem. Some of the posts suggested that I reinstall software-center. But even that does not work. So here is the output of invoking software-center from commandline:

```

$software-center
2012-10-11 18:46:49,925 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-11 18:46:50,010 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-11 18:46:51,521 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-11 18:46:51,765 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-10-11 18:46:51,787 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

```
And then, it just hangs waiting for something. The software-center window opens up. But nothing on it is visible.

When invoke software-center as root, I get the following output. 
```

$ sudo software-center
2012-10-11 18:51:48,891 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-11 18:51:48,894 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-11 18:51:49,268 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-11 18:51:49,410 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-10-11 18:51:49,412 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-10-11 18:51:53,866 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2012-10-11 18:51:57,080 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-10-11 18:51:57,080 - softwarecenter.db.database - INFO - reopen() database
2012-10-11 18:51:57,080 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

```
Now the software-center window opens up and everything is visible. 

So where do you think the problem is? Do you have any suggestions?

Thanks
Xlearner

---

### Post by xlearner on 2012-10-16
Can someone please help me with this problem? Normally, I use ubuntu software-center to install debian files with .deb extensions. Due to this problem, I don't know how to install them. Any suggestions.

Thanks
Xlearner

---

