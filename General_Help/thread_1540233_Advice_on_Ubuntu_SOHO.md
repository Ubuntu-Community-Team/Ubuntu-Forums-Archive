---
title: "Advice on Ubuntu SOHO"
date: 2010-07-27
forum: General Help
---

### Post by riprowan on 2010-07-27
I've read several of the old posts here on this topic, and find them largely contradictory, confusing, and / or out of date.

I'd like a simple Ubuntu based SOHO solution - file and print sharing, simple access to files from the Internet / FTP, UPnP media storage, etc.  The sort of stuff you get with a Windows Home Server, only without the Windows.

I would prefer to start with Ubuntu desktop as I want the GUI and want to keep it as super-simple as possible, but since it will be in a DMZ it also needs to be reasonably secure.  Is this possible?

Is there a guide for dummies out there that can help me out?

---

### Post by bodhi.zazen on 2010-07-27
Yes you can do all this.

In general a GUI is of little to no help on a Server, most of what you do is either restarting services or editing config files.

If you want a graphical interface use Webmin.

For file sharing use Samba.

For detailed instructions see :

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Webmin  - [http://woodel.com/](http://woodel.com/)

---

### Post by drdos2006 on 2010-07-27
I found this HOWTO very informative.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

