---
title: "Pytrainer will not run on Ubuntu 11.04"
date: 2011-04-28
forum: General Help
---

### Post by _sAm_ on 2011-04-28
Hi

The program Pytrainer([http://sourceforge.net/apps/trac/pytrainer/](http://sourceforge.net/apps/trac/pytrainer/)) will not start on Ubuntu 11.04. I have tried on two different computers with same result. 

I have tried to run it from the "dash" and from the terminal. Terminal (only) outputs:
data_path: /usr/share/pytrainer/
DIR: /usr/share/locale
site_path: /usr/lib/python2.6/site-packages

Pytrainer worked fine on Ubuntu 10.10.

Help is appreciated

---

### Post by _sAm_ on 2011-04-30
I tried Kubuntu live mode and installed pytrainer - and it worked!

I downloaded and installed pytrainer from the the homepage, on my Ubuntu desktop, and now its working.

---

### Post by drader on 2011-08-06
I've got the same thing, no work in ubuntu 11.04 but it did in 10.x.

A bit more info:
```
drad@alexei:~$ pytrainer
running pytrainer from egg installation
data_path: /usr/local/share/pytrainer/
gettext_path: /usr/local/share/locale
site_path: /usr/local/lib/python2.7/site-packages
Using xulrunner dir: /usr/lib/xulrunner-2.0
Traceback (most recent call last):
  File "/usr/local/bin/pytrainer", line 121, in <module>
    main()
  File "/usr/local/bin/pytrainer", line 118, in main
    pytrainer = pyTrainer(None, data_path)
  File "/usr/lib/pymodules/python2.7/pytrainer/main.py", line 159, in __init__
    self.windowmain.createGraphs(RecordGraph,DayGraph,WeekGraph, MonthGraph,YearGraph,HeartRateGraph)
  File "/usr/lib/pymodules/python2.7/pytrainer/gui/windowmain.py", line 139, in createGraphs
    self.drawarearecord = RecordGraph(self.record_graph_vbox, self.window1, self.record_combovalue, self.record_combovalue2, self.btnShowLaps, self.tableConfig)
  File "/usr/lib/pymodules/python2.7/pytrainer/gui/SimpleGladeApp.py", line 71, in __getattr__
    raise AttributeError, data_name
AttributeError: tableConfig
```

---

### Post by drader on 2011-08-06
After a little more digging I found *a solution*. I tried the following steps, the last provided my solution (**NOTE: be sure to back up your pytrainer data directory [~/.pytrainer] before you do any of the following**):
[LIST=1]
[*]Reinstalled pytrainer through synaptic (no change - did not work)
[*]Uninstall/Purge through synaptic, install pytrainer from synaptic (no change - did not work)
[*]Uninstall/Purge through synaptic, download/installed pytrainer 1.8.0 from [sourceforge]("http://sourceforge.net/projects/pytrainer/files/") (pytrainer started, all data intact)
[/LIST]

All of my previously entered pytrainer data was intact so I did not need my backup of the data directory; however, I'd still recommend doing it.

Of course, one side effect to fixing the problem the way I have listed above is that pytrainer will no longer be installed through the package manager so you will not get updates through the package manager. This is a tradeoff I'm willing to take as pytrainer was not working before and it is now.

---

### Post by digitography on 2011-08-06
I have just started using pyTrainer, and I have to say what a great piece of software, makes the Garmin Training Centre look very poor.
I was able to export all my data from Garmin TC and import it into pyTrainer, worked great.
I am a little concerned that there is no backup utility in pyTrainer, is simply copying .pytrainer folder a viable alternative?

---

### Post by digitography on 2012-02-27
I have moved on somewhat since my last post.
New PC, 11.04 but not using the dash interface.
Installed pytrainer without any problems, except 1 stupidly annoying one:
By default pytrainer 1.7.2 starts with google maps v3 by default, (the switch --gmaps2 doesn't work), so how can I use it with google maps v3, what is that a library or a plugin, what?
If I manually turn the google maps v3 off with 
Edit[INDENT]Preferences[INDENT]Startup Parameters tab
[/INDENT][/INDENT]then it works fine, but I have to do that everytime I start the program.

it's just irritating.
any help as always appreciated.

---

