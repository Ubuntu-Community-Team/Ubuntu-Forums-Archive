---
title: "How to install a program for all users"
date: 2010-05-12
forum: General Help
---

### Post by notbitmonk on 2010-05-12
I bought QCAD after having spent more than a year with the community edition.  -- Cheap and wonderful CAD software --  The download just unzips and I just need to run a file to start QCAD.  Problem is that unlike the community edition at the repositories, this one does not installs itself.  The computer I have has four accounts set up.  One is the administrative account which i use to install and perform maintenance.  The other three are regular users (me, my wife and daughter).  What I would like to do is install the software and then add an entry on the menu that propagates to all users.  Most likely I would install it in the /opt folder.  The questions are:
[LIST=1]
[*]What permissions do I need to set?
[*]How do I create an entry in the Applications list that propagates to all users?
[/LIST]
The same thing happens with Lightscribe.  It installed itself in the /opt folder but did not create an entry for any user.  I also bought the [www.wolfire.com/humble](www.wolfire.com/humble) package of games (great package for linux gamers) and may end up needing such advise.

---

### Post by gzarkadas on 2010-05-12
> **notbitmonk said:**
> What permissions do I need to set?

Typically (ls -l style):
```
-rwxr-xr-x   root   root    <your executable>
```That is owner and group is `root', owner has full permissions to the executable, group and others have read and execute only permissions.

You can use the command
```
sudo chmod 755 <your executable>
```to set the permissions.

For non executable files (such as config, data, etc) omit the x bit, ie use 
```
sudo chmod 644 <your other file>
```to set the permissions.

> **notbitmonk said:**
> How do I create an entry in the Applications list that propagates to all users?

Pick up the most close to your case `.desktop' file inside `/usr/share/applications' and copy it to `/usr/local/share/applications' under a name that you choose. Ensure group and other users have read permissions to this file. Now open the file in a text editor and modify the fields you see to load the installed application and show the appropriate menu text. Logout and Login back again to see the menu appear in your menubar.

---

