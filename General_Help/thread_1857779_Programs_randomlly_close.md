---
title: "Programs randomlly close"
date: 2011-10-11
forum: General Help
---

### Post by PrfJennings on 2011-10-11
Howdy, programs such as the install manager the computer janitor, firefox and others will launch for a couple seconds then immediately close. I launched one of them using termnal and this is the error. 

samuel@samuel-desktop:~$ gksudo software-center
2011-10-08 12:42:34,692 - root - WARNING - failed to add sca db Couldn't  stat '/root/.cache/software-center/software-center-agent.db' (No such  file or directory)
/usr/share/software-center/softwarecenter/app.py:1191: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-10-08 12:42:35,267 - softwarecenter.fixme - WARNING - logs to the  root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367,  'reconnect_monitors')'
2011-10-08 12:42:35,267 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50:  Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-10-08 12:42:36,300 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2011-10-08 12:42:36,300 - softwarecenter.db.update - WARNING - error: Operation not supported
samuel@samuel-desktop:~$

---

### Post by wildmanne39 on 2011-10-11
Hi, I have found some bug reports on this issue.
```
sudo rm /var/cache/apt/*.bin
```
[http://ubuntuforums.org/archive/index.php/t-1766426.html](http://ubuntuforums.org/archive/index.php/t-1766426.html)
That command was given as a fix for this problem in software center, please go to the link and look yourself also.
Thank you

---

### Post by PrfJennings on 2011-10-11
You sir, are awesome. This isn't the first time you've helped me, thanks a ton.

---

### Post by wildmanne39 on 2011-10-11
Hi, you are welcome! I am happy I could help.
Enjoy

---

