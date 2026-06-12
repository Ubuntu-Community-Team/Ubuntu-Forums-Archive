---
title: "backintime"
date: 2009-11-19
forum: General Help
---

### Post by nunki on 2009-11-19
Im using backintime to do my local backups. I wanted to take advantage of its user.callback functionality, so I wrote a small shell script to email me the results of the backups when they occur.

If I run the shell script on the command line directly, it works. If I open backintime gui and click the "Take Snapshot" button, it also works. However, the automated scheduled backups never seem to trigger the callback. I've looked in syslog, and I can see that it is being called, but alas, no email.

Before I file a bug report, I wanted to see if anyone else has had issues with this functionality.

---

### Post by fluffman86 on 2009-11-19
Make sure you're using complete paths in your crontab.  That's been causing problems recently.

---

### Post by nunki on 2009-11-19
The backintime program is what makes the entries in crontab. When any backups occur it is supposed to look for $HOME/.config/backintime/user.callback and execute it if it exists. This only seems to happen when using the gui.

The crontab entry doesnt define the location of this callback. The underlying python code is hardcoded to look for this file in this location.

---

