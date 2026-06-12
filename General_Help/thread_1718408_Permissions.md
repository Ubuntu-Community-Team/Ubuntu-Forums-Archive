---
title: "Permissions"
date: 2011-03-31
forum: General Help
---

### Post by Ziton on 2011-03-31
I have Ubuntu 10.10 and mythtv. I am trying to get recordings to appear in "watch recordings". I went to var-lib-mythtv-recordings to watch a recording.
It wont play so I checked the properties and permissions. It says "You are not the owner, So you cannot change these permissions"
I'm logged in as adminastrator and I'm the only one with access to this computer.
I cant find a way to change the permissions. Anybody know?

---

### Post by deathadder on 2011-03-31
Just because you're logged in as root (not something you should be doing btw) it doesn't mean you automatically have permission to view a file. 

From a terminal you can change the permissions of a file using the "chmod" command. 

You may want to have a look at the mythtv wiki pages:
[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)
[http://www.mythtv.org/wiki/User_Manual:Daily_Use](http://www.mythtv.org/wiki/User_Manual:Daily_Use)

---

### Post by jerome1232 on 2011-03-31
If you mean your logged into the administrators account (meaning in my mind a user authorized to use sudo to elevate to root privilages)

Then you need to use chmod, only preprend the chmod command with sudo. IE if you wanted to give the user and group rw access:

```
sudo chmod ug+rw filename
```

---

