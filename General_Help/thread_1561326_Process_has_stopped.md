---
title: "Process has stopped"
date: 2010-08-26
forum: General Help
---

### Post by Gordonisnz on 2010-08-26
Hi,

I've come accross a problem.

Basically, i've got a Nginx server running on my Ubuntu 10.04 (lucid) system.

Ive used gedit to open up the error log for nginx, & another file. & it has stopped (gedit).

i can minimise / maximise the gedit programme, But I cant edit / close / save / shut down or anything to the file.  

I'm running System Monitor & gedit doesn't appear in the processes.

I *can* use other programmes, & everything else seems to be working  OK.

Query :- How do I close / stop / end / reset / Kaboom the gedit programme, So I can re-open the files & use gedit (again).

---

### Post by HereInOz on 2010-08-26
If gedit is truly not in the System Monitor process list, then you could try Right Alt plus Print Screen, then tap the k key.  This will restart gnome.  

Or you could open a terminal and type:

ps aux | grep gedit

This will give you the process ID in the left column, then use kill <processID> to stop it.

---

### Post by Gordonisnz on 2010-08-26
thanks - ps aux / kill  worked 

( I'm used to the old WINXP system..- still learning Linux)..

---

