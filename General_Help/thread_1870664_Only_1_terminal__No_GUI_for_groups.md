---
title: "Only 1 terminal?  No GUI for groups?"
date: 2011-10-27
forum: General Help
---

### Post by hsweet on 2011-10-27
WTF?  I recently upgraded my 3 version old system.  It's been ok, no big issues.  But today I noticed that I can only open a single terminal in Unity.  There are lots of times I need more than 1.  So I figure I'll just run screen.  Not installed so I use my poor single terminal to run ```
sudo apt-get install screen
``` and damned if I get "unable to locate package screen!"

I know I still have Alt1-6 but that slower and I have to log in again.

Then user accounts has been simplified to the point that there is no GIU access to groups.  They are still there, but no way to get at them without CLI?  

I can't think of a good reason to limit access to the command line.  If you are not comfortable there, use Unity and be happy.  But I can't see why making the interface simple should preclude knowledgeable users from taking care of business.

---

### Post by wolfen69 on 2011-10-27
When you open a terminal, you will see it on the left (dash). Just right click the terminal icon and choose *new window*. Not sure about groups.

---

### Post by coffeecat on 2011-10-27
Four ways to open two or more terminals in Oneiric Unity when one is open already.

Middle-click on terminal launcher in dock.
Right-click on open terminal -> Open terminal
Shift-Ctrl-N
Terminal menu -> File -> Open Terminal

The package screen is in the repositories - in the main repository, no less. Try a sudo apt-get update and see if it appears.

The problem with the User Accounts utility in an upstream gnome one. Don't blame Ubuntu or Unity. You can install the gnome 2 package gnome-system-tools to get the older Users and Groups app. As far as I can make out it works OK in Oneiric and will have to do until the upstream gnome people further develop the gnome 3 users utility.

---

