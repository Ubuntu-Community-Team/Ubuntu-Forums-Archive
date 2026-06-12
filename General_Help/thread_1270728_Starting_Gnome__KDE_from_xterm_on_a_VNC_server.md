---
title: "Starting Gnome / KDE from xterm on a VNC server"
date: 2009-09-19
forum: General Help
---

### Post by AsoSako on 2009-09-19
Alright so I am connecting to another linux system trhough vnc, but all I get is an xterm.  I know that it has both gnome and kde available so I was wondering if anyone can tell me if there is a way to start gnome / kde trhough xterm while keeping the vnc server on the system running.

---

### Post by infurnus on 2009-09-20
Although you may have specific reasons for VNC. I have always, and will always, use NoMachine NX for remote access to my linux machines. You spawn your own session and it is implemented over ssh.

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

food for thought.

---

### Post by kevdog on 2009-09-20
Just a suggestion, but you can forward X sessions through an ssh connection rather than using VNC.  FreeNX is an optimized way to do this, but even without FreeNX you can forward Gnome/KDE/XCFE desktops.  Id really recommend forwarding a very basic desktop such as xcfe rather than a bulkier gnome or kde session since speed is definitely an issue.

---

### Post by AsoSako on 2009-09-20
Thanks for the advise, I would keep it in mind for my own Linux servers, however the server I am referring to is not my own, and my user account is not on the sudoers file thus i'd have a hard time doing this.  What I need is a way to start Gnome / KDE from XTerm.

---

### Post by jdieter on 2010-11-08
Is there is a way to start gnome / kde through xterm. I am using putty and Xming to connect to my server. I can start xterm, and would like to start gnome / kde. Is this such a hard question? or impossible?

---

