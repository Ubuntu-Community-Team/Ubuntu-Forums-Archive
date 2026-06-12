---
title: "Need help with mysql and permissions"
date: 2011-09-25
forum: General Help
---

### Post by bakan723 on 2011-09-25
ok guys so I have used linux before but not that much and I used to be a heavy windows user until I made my switch.  Now I run this server for a soccer game Pro evolution.

The soccer server is called Fiveserver and it requires mysql and a database.  I have created the database and set up the schema file provided with fiveserver.  

to run this fiveserver i have a file named run in /services/fiveserver.  when i double click the run file it asks me if I want to display, run, run in terminal, or cancel.  

When I run in terminal a terminal window pops up and then dissapears

When I just click run it seems to do nothing

But when i open a terminal window and drag the run file in there it gives me this message but server seems to still not be running. 



brock@brock-Linux:~$ '/service/fiveserver/run' 
touch: cannot touch `/var/log/fiveserver/fiveserver.log': Permission denied
chown: changing ownership of `/var/log/fiveserver/fiveserver.log': Operation not permitted
chgrp: changing group of `/var/log/fiveserver/fiveserver.log': Operation not permitted
Traceback (most recent call last):
  File "/usr/bin/twistd", line 19, in <module>
    run()
  File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 27, in run
    app.run(runApp, ServerOptions)
  File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 631, in run
    runApp(config)
  File "/usr/lib/python2.7/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
    _SomeApplicationRunner(config).run()
  File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 376, in run
    self.logger.start(self.application)
  File "/usr/lib/python2.7/dist-packages/twisted/application/app.py", line 216, in start
    observer = self._getLogObserver()
  File "/usr/lib/python2.7/dist-packages/twisted/scripts/_twistd_unix.py", line 139, in _getLogObserver
    logFile = logfile.LogFile.fromFullPath(self._logfilename)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 49, in fromFullPath
    os.path.dirname(logPath), *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 162, in __init__
    BaseLogFile.__init__(self, name, directory, defaultMode)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 41, in __init__
    self._openFile()
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 167, in _openFile
    BaseLogFile._openFile(self)
  File "/usr/lib/python2.7/dist-packages/twisted/python/logfile.py", line 65, in _openFile
    self._file = file(self.path, "r+", 1)
IOError: [Errno 13] Permission denied: '/var/log/fiveserver/fiveserver.log'
brock@brock-Linux:~$ 

Could anyone possibly help me out im so stuck here and I heard you guys in the Ubuntu forums were real helpful

---

### Post by patryk77 on 2011-09-25
> **bakan723 said:**
> [...]I heard you guys in the Ubuntu forums were real helpful

We are... But please try and keep it in [one thread](http://ubuntuforums.org/showthread.php?t=1849091) ;) ... There is already a reply there.

---

