---
title: "Menu Problems"
date: 2011-05-25
forum: General Help
---

### Post by jiminy_cricket on 2011-05-25
I am running Ubuntu 11.04 on my desktop and on my netbook. On the desktop Ubuntu has a menu in the top bar which allows me to access all applications. On the netbook, I don't have this.

How do I get the menu bar on the netbook?

I'm finding that as I go through online tutorials the things referred to don't appear on my netbook Ubuntu, I know that the netbook edition is probably a stripped back Ubuntu for performance reasons but how can I get some of this functionality back?

---

### Post by jerryjustly on 2011-05-25
I've noticed on two different laptops of mine, the Ubuntu features appear different upon install too.  You might try changing the type of desktop you are using.  To do this, press Alt + F2. Then paste the following into the text box and press enter:
gnome-session-save --force-logout
Once to the log in screen. If your computer is like mine, there still are no desktop options to be seen anywhere. At this point press Enter two times, and the desktop options will show up at the bottom of the screen. Choose the one you want(for instance classic is just like Ubuntu 10.10 default) and then log back in.

------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by 3rdalbum on 2011-05-26
It sounds like your desktop is running the Ubuntu Classic session, and your netbook is running the Ubuntu (Unity) session.

You can change your desktop to Ubuntu (Unity) or your netbook to Ubuntu Classic by logging out, clicking your name on the login screen, changing the Session popup menu at the bottom of the screen, typing your password and then logging in.

Ubuntu Classic is now unmaintained software and will disappear in Ubuntu 11.10, so you might want to get used to using Unity.

A lot of older tutorials for Ubuntu assume you'll be using Ubuntu Classic, so maybe try and find more recent tutorials or convert the instructions into something that makes sense in Unity.

---

