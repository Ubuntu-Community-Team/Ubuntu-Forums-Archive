---
title: "Unable to launch a .sh from an Application Shortcut"
date: 2010-09-01
forum: General Help
---

### Post by SmartTech on 2010-09-01
Hey All,

I'm new here, but certainly not new to Linux. Some of you may recognise my screen handle from other forum groups. Sadly my other communities seem to be dying and this one is going strong so here I am!

I'm sure there's something I'm doing incorrectly, but here's my scenario:

I have a pair of shell scripts that launch SSH sessions with different  forwarded ports, and use them multiple times each day. I'd like to drag  the shell script directly onto the top Ubuntu Bar where shortcuts go and  be able to use it. Or, even better, put all of my frequently used shell  scripts in a "drawer". I know that I used to be able to make a  shortcut, and set its path to "gnome-terminal -e file://xx.sh" and the  script would run in a new terminal window. 

When I try to do this, a terminal opens with an error dialog that reads  "There was an error creating the child process for this terminal".  Permissions?

Thanks for looking!
Pete

---

### Post by SmartTech on 2010-09-01
Bump. Wow, there are a lot of new threads today!

---

### Post by apmcd47 on 2010-09-01
Stupid question, as I'm not a gnome user: Have you made the scripts executable?

Andrew

---

### Post by ankspo71 on 2010-09-01
Hi,
Have you already tried opening them with sh?
```
sh /path/to/script.sh
```
I sometimes create menu shortcuts like that.
Hope this helps.

---

### Post by SmartTech on 2010-09-01
Thanks for looking at least!

The scripts ARE executable, and right clicking and selecting properties declares its of type shell script (application/x-shellscript) Permissions  have been full 777.

As a temporary workaround, I have the Folder on the quicklaunch area. I can double click the script, and select "Run in Terminal" and it behaves perfectly.

---

### Post by SmartTech on 2010-09-01
Ankspo - This may be helpful! I never thought to use sh directly, but I replaced the 'gnome-terminal -e' with sh, and.... nothing. I can click the icon, but nothing happens.

I can NOT create a shortcut for a shell script it seems!

---

### Post by SmartTech on 2010-09-02
Bump :-)

---

### Post by SmartTech on 2010-09-08
Is there anyone running Ubuntu 9.04+ that is able to create a working shell script, AND make a shortcut/launcher for it in Gnome? 

I'm unsure if its a Gnome thing or not, but my RHEL5.5 system at home with KDE doesn't have a problem. There are so many differences between these machines that it isn't a fair comparison though.

---

### Post by ubulal on 2010-09-08
Can you post one of the scripts here?

---

### Post by TwelveGauge on 2010-09-08
terminal:
```
./whatever.sh
```that's as close as you're going to get in terms of a shell script 'shortcut'. If it's something you want to run all the time, why not make it a start up application?

---

### Post by me01273 on 2012-01-18
I know this is a bit outdated, but it showed up first in google when I searched for "shortcut launch sh script in bash".

After lots of searching I found out you just need to do "gnome-terminal -e /loc/to/file/xx.sh" and it runs fine.

David

---

### Post by oldos2er on 2012-01-18
Closed, necromancy.

---

