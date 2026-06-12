---
title: "tsclient Desktop/Cairo Dock Shortcut"
date: 2010-12-22
forum: General Help
---

### Post by smuthavarapu on 2010-12-22
This post will explain how to create a TSClient / RDP short cut which will open the server Directly

Once you fill up all the entries for the TSClient then Client "Save As" in Quick Connect. 


The file will be stored in /home/smuthavarapu/.tsclient/xxxx.rdp


Then use following command 


tsclient -x ~/.tsclient/xxxx.rdp


Make it a Launcher and add it to Desktop / Cairo Dock.

Right click on the Desktop and Create a Launcher.

give the command tsclient -x ~/.tsclient/xxxx.rdp
this will open the Server directly, which out clicking the Connect button again.

Drag and Drop this short to Cairo Dock

In Cairo Dock I am giving the entries for the Icon.


Launcher name : MyWindowServer
Command to run on Click : tsclient -x ~/.tsclient/xxxx.rdp
Image's name or Path : /ur/share/icons/Humanity/apps/48/tsclient.svg
-------------
Extra Parameters 
-------------
Class Name : rdesktop

---

