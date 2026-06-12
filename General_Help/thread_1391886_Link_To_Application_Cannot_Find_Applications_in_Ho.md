---
title: "Link To Application Cannot Find Applications in Home Folder"
date: 2010-01-27
forum: General Help
---

### Post by JPStevens on 2010-01-27
I seem to be seeing some weird behavior in kubuntu with KDE 4.3.2 and KDE 4.3.5 for Kubuntu 9.10 32-bit.

I have a few programs in my home folder. For instance Eclipse and Mendeley. it seems that when i create a Link to Application does not launch them. Here is how I create the links.

-> I right click and create a new "Link to Application"
-> I click on the Application tab and browse to where the shell script, or executable is. 

and when I try to launch them it does not work. The link is using the absolute path. I tried setting the working directory and using a relative path but nothing. If I run the link in a terminal it says "Warning: Could not find" and the application I set. Now this seems to not be a problem for system applications like Kate. If i change the link to launch Kate it works perfectly.

I tried to google for if there is a bug, but nothing came up

---

### Post by hwttdz on 2010-01-27
Could you post the exact output of one of the "could not find" errors from the terminal.  And then also the output of "ls -F /path/to/app/".

---

