---
title: "Software center or Computer Janitor won't launch"
date: 2011-10-08
forum: General Help
---

### Post by PrfJennings on 2011-10-08
Hello, I turned on my PC today and I can't get my software center or the comp janitor to run, I also am missing one of the programs I installed. This is the error I get when I try to launch it through terminal. 

samuel@samuel-desktop:~$ gksudo software-center
2011-10-08 12:42:34,692 - root - WARNING - failed to add sca db Couldn't stat '/root/.cache/software-center/software-center-agent.db' (No such file or directory)
/usr/share/software-center/softwarecenter/app.py:1191: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-10-08 12:42:35,267 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-10-08 12:42:35,267 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-10-08 12:42:36,300 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2011-10-08 12:42:36,300 - softwarecenter.db.update - WARNING - error: Operation not supported
samuel@samuel-desktop:~$ 

Thanks in advance.

---

