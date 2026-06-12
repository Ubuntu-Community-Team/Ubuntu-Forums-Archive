---
title: "glxgears is not working"
date: 2010-02-22
forum: General Help
---

### Post by DrDaveyAtoms on 2010-02-22
Hope someone can help me. When I run glxgears I get the following message:

```
dave@dave-laptop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```I guess this is indicative of an underlying problem with X11. However, I have no idea how to solve this or, indeed, where to start.

Any help appreciated.

---

### Post by ajgreeny on 2010-02-22
Have a look at your hidden xsession-errors file in home.  In a normal install of ubuntu it will be only a few Kb in size, rising fast when errors occur.  Mine has never gone above about 1Mb, and that was when a repeating error appeared after trying an impossible task.

The file can be a bit hard to decode what is meant, and there are often a number of spurious errors shown, which are either unimportant or are not even errors at all, but simply logs of what happened.  It may, however, give you a clue about where to start looking.

You could also try purging, and reinstalling mesa-utils, which is the package containing glxgears.

---

### Post by DrDaveyAtoms on 2010-02-22
Thanks for the advice. The .xerror-session file is 6.4 kB in size.

I suspect that this is related to the fact that I cannot activate the ATI/AMD proprietary FGLRX drivers.

They seem to be installed:

[CODEdave@dave-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.][/CODE]

I then try to activate the drivers by going to System -> Administration -> Hardware Drivers. Upon pressing the Activate button I get the message > Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.logHas anyone else experienced this issue?

---

### Post by DrDaveyAtoms on 2010-02-22
I was able to solve this problem by trawling through the google search results. The solution, in case you come across this post, can be found at [http://nava-azura.blogspot.com/2009/03/installing-atiamd-proprietary-fglrx.html](http://nava-azura.blogspot.com/2009/03/installing-atiamd-proprietary-fglrx.html)

Now I have glxgears working!!

---

