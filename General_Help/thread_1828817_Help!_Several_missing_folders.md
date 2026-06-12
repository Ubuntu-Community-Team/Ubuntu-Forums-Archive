---
title: "Help! Several missing folders"
date: 2011-08-19
forum: General Help
---

### Post by lemonlime67 on 2011-08-19
After rebooting my system my documents, downloads, and music folders suddenly "disappeared." The videos folder also managed to empty itself. 

I haven't been tinkering with anything, except to kill/re-install  banshee which hadn't been working earlier. I'm a new user so I don't know if this would be related to my problem but in one of many attempts to get banshee to start working again I ran this command in terminal: 

rm -rf ~/ .gconf/system/gstreamer

Again, I haven't had Ubuntu for too long so any help on why the folders disappeared would be appreciated. Thanks!

---

### Post by sanderd17 on 2011-08-19
you typed a space after the slash (/), is that right?

if you do rm -rf ~/ , that means "remove your home", bash won't look any further than the slash.

---

### Post by pqwoerituytrueiwoq on 2011-08-19
if you lost anything important i would boot a live cd and try a data recovery app like test disk

---

### Post by lemonlime67 on 2011-08-19
I did put a space. That sounds problematic and is probably a sign that I should stop copying commands that I don't understand. Is there any way to recover my home folder from that command?

---

### Post by sanderd17 on 2011-08-19
if you shut down your computer now, there is a chance that it's not overwritten yet and you can recover it with some tools like these: [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I can't promise anything though.

To stay out of future problems, read this short tutorial: [linuxcommand.org]("http://linuxcommand.org") The first part about the CLI will be enough, you don't need to learn to write shell scripts.

---

### Post by lemonlime67 on 2011-08-19
Ok I just restarted my computer and the folders are back, but still empty so I guess I will try using a live CD to recover my stuff. Thanks for all the help

---

### Post by sanderd17 on 2011-08-19
They are back only because Ubuntu creates them on the first boot (or in case they are missing).

---

