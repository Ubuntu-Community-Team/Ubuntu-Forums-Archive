---
title: "software-center"
date: 2012-01-08
forum: General Help
---

### Post by bluexrider on 2012-01-08
Running 11.04 

Ubuntu Software Center no longer shows 'History' 

I confirmed all the PPA's are current and the installed software is correct but I cannot 'see' the history. 

The spinning GIF just keeps on spinning...

---

### Post by bluexrider on 2012-01-08
```
2012-01-08 11:51:09,798 - softwarecenter.app - INFO - software-center-agent finished with status 1
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 115, in rescan
    self.transactions = cPickle.load(open(p))
ImportError: No module named history
```

this happens as a normal user. 

I can get the 'history' to show if using software-center as ROOT

---

### Post by bluexrider on 2012-01-08
reinstalled software-center and ran as 'ROOT'
```

2012-01-08 12:35:30,133 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 154, 'open')'
2012-01-08 12:35:30,132 - root - WARNING - failed to add sca db Couldn't stat '/root/.cache/software-center/software-center-agent.db' (No such file or directory)
2012-01-08 12:35:30,541 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2012-01-08 12:35:30,540 - root - WARNING - No styling hints for elementary were found... using Human hints.
/usr/share/software-center/softwarecenter/app.py:1194: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2012-01-08 12:35:33,170 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/zeitgeist/client.py', 397, 'reconnect_monitors')'
2012-01-08 12:35:33,147 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
/usr/share/software-center/softwarecenter/apt/aptcache.py:45: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main_iteration()
2012-01-08 12:35:39,605 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2012-01-08 12:35:39,606 - softwarecenter.db.update - WARNING - error: Operation not supported
2012-01-08 12:35:40,047 - softwarecenter.app - INFO - software-center-agent finished with status 1
```

---

### Post by bluexrider on 2012-01-08
```
rm -rf  ~/.cache/software-center
```

now working

---

