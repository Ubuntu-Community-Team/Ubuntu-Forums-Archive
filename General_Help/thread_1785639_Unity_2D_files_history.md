---
title: "Unity 2D files history"
date: 2011-06-18
forum: General Help
---

### Post by garagestmarien on 2011-06-18
I am running and happy with unity 2D on Ubuntu 11.04.
(Graphics card won't let me use full Unity or Gnome 3).
On the left panel there is a files and folders button that when clicked shows the history of recently opened files.
Is there a way to clear this? or am I stuck with it remembering everything that has been opened.

---

### Post by Rubi1200 on 2011-06-18
Open a terminal and run these commands:

```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```

Then logout and back in again.

---

### Post by garagestmarien on 2011-06-18
[B]Thanks for the info, I have followed the instructions, but I don't know if something is sticking. The results from my terminal are below and it doesn't seem to matter how long I wait, nothing more happens.
I did log out and back in again, but no file history was cleared, I also tried re-booting, but that didn't help either and I tried running the commands again, but with the same results.[/B]

[2011-06-19 03:32:23,353] - DEBUG - singleton - Checking for another running instance...
[2011-06-19 03:32:23,364] - DEBUG - root - Replacing currently running process...
[2011-06-19 03:32:23,588] - INFO - zeitgeist.sql - Using database: /home/john/.local/share/zeitgeist/activity.sqlite
[2011-06-19 03:32:23,590] - DEBUG - zeitgeist.sql - Updating sql schema
[2011-06-19 03:32:25,595] - INFO - zeitgeist.sql - DB set up in 2006.69598579ms
[2011-06-19 03:32:25,596] - DEBUG - zeitgeist.extension - Searching for system extensions in: /usr/share/zeitgeist/_zeitgeist/engine/extensions
[2011-06-19 03:32:25,597] - DEBUG - zeitgeist.extension - Searching for user extensions in: /home/john/.local/share/zeitgeist/extensions
[2011-06-19 03:32:25,712] - DEBUG - zeitgeist.extension - No extra extensions
[2011-06-19 03:32:25,713] - DEBUG - zeitgeist.extension - Found extensions: [<class '_zeitgeist.engine.extensions.fts.SearchEngineExtension'>, <class '_zeitgeist.engine.extensions.blacklist.Blacklist'>, <class '_zeitgeist.engine.extensions.datasource_registry.DataSourceRegistry'>]
[2011-06-19 03:32:25,713] - DEBUG - zeitgeist.extension - Loading extension 'SearchEngineExtension'
[2011-06-19 03:32:25,714] - DEBUG - zeitgeist.fts - Opening full text index: /home/john/.local/share/zeitgeist/fts.index
[2011-06-19 03:32:25,725] - DEBUG - zeitgeist.extension - Loading extension 'Blacklist'
[2011-06-19 03:32:25,726] - DEBUG - zeitgeist.blacklist - No existing blacklist config found
[2011-06-19 03:32:25,735] - DEBUG - zeitgeist.extension - Loading extension 'DataSourceRegistry'
[2011-06-19 03:32:25,741] - DEBUG - zeitgeist.datasource_registry - Loaded data-source data from /home/john/.local/share/zeitgeist/datasources.pickle
[2011-06-19 03:32:25,754] - INFO - root - Trying to start the datahub
[2011-06-19 03:32:25,798] - DEBUG - root - Running datahub (/usr/bin/zeitgeist-datahub) with PID=4995
[2011-06-19 03:32:25,799] - INFO - root - Starting Zeitgeist service...


**UPDATE/ Now my panel no longer hides!**

---

### Post by Rubi1200 on 2011-06-19
Okay that is strange because it works for me. I ran the first command and then the second one before closing the terminal and logging out.

As for the panel, what happens if you move the mouse to the upper left? Does it hide?

This may be a problem specific to Unity-2D. I will see if I can find more information about this.

---

### Post by garagestmarien on 2011-06-19
What happened was that the unity panel was fixed on screen and would not hide.
So when I opened a window, it went underneath the panel, the panel would not auto hide.
But I have solved this by un-installing and re-installing unity 2D.

---

### Post by Rubi1200 on 2011-06-19
Sorry you had to go through this trouble, but at least you found a solution for the moment.

I have noticed some other odd things with Unity, but am hoping these issues will be worked out for the next release in October.

---

