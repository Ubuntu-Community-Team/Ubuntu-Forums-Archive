---
title: "software installation"
date: 2011-05-26
forum: General Help
---

### Post by Rakeshvijayan on 2011-05-26
let me know friends if  install any package on ubuntu where it placed I mean if  in windows 
all installation file goes to the programfiles like were in ubuntu .and how we use that package on crone scheduling .deluge is torrent download r , I need deluge  path for schedule for 
automaticaly start the application

---

### Post by 3rdalbum on 2011-05-26
On Linux, parts of a program go where they are needed to go in order to be recognised or re-used by other programs.

If you want to know what location a particular program is in, find its package in Synaptic Package Manager, right-click on it, choose Properties and then go to Installed Files tab.

EDIT: Transmission has a function built-in where you can start and stop it at specific times. This will prevent you from having to mess around with your crontab. Maybe try Transmission instead of Deluge?

---

### Post by Rakeshvijayan on 2011-05-26
j

---

### Post by Rakeshvijayan on 2011-05-26
This is one of the knowledge for me that why I following back to the deluge I am attaching the screen shot of the installed file .help me which path I can choose form there, for starting the application by  the command

---

### Post by oldos2er on 2011-05-26
I think you're looking for /usr/bin/deluge 
Since /usr/bin is in your $PATH, you only need to type **deluge** to start the program.

---

### Post by Rakeshvijayan on 2011-05-27
Is it enough to give any package name instead of the path in cronetab 

04 2 * * *  deluge

---

