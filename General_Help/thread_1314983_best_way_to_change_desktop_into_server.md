---
title: "best way to change desktop into server?"
date: 2009-11-04
forum: General Help
---

### Post by badperson on 2009-11-04
Hi,
I have a desktop machine right now that is dual booted with vista and ubuntu 9.10. 

I really like the machine, but I had another machine I was using as a server that died. I would like to take my current desktop and turn it into a server running a LAMP install of ubuntu, and then build another machine for a desktop. (I don't DESPERATELY need a server...I just think it's cool, besides, I can have a filesharing space I can get to from my laptop as well. CVS was the main thing I used it for, and it was really handy for that)

I was thinking it may just be best to back up everything I have and completely start from scratch. I have a lot of photographs and music on my desktop now, that I want to be on my server. Also, I use iTunes and would like to have the library be on the remote machine (not a linux question, I realize)

Is it possible to install ubuntu server over the partions that exist now? I won't do this over the weekend or anything...probably around March or so, but wanted to start thinking about it. 
bp

---

### Post by x C0MMAND0 x on 2009-11-04
You could [download Ubuntu Server ]("http://www.ubuntu.com/getubuntu/download-server").  You could then use something like Darik's boot and nuke to completely wipe your HD of everything and then reinstall Ubuntu Server, or you could use Gparted to erase everything and then install Ubuntu Server.

Or, Ubuntu Server install might have an option to use entire HD which will do this all for you (I haven't installed it so I'm not sure about this)

---

### Post by michy99 on 2009-11-04
Here's some links for reading:

[http://www.ubuntugeek.com/installing-lamp-using-taskeldesktop-edition.html](http://www.ubuntugeek.com/installing-lamp-using-taskeldesktop-edition.html)
[http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-lamp-server-setup.html)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by wildweathel on 2009-11-04
Mail server, GNOME desktop, KDE, LAMP, all these things are simply software installed on the base Ubuntu system.  Thus, an install can be many of these things.  My computer, for example, is an apt cache server, a desktop Ubuntu system, *and* a desktop Xubuntu system all at once.  The "server" installer simply gives you a minimal Ubuntu system running on a slightly differently tuned Linux kernel.

There's no need to reinstall.  Just install the server packages you want.  If you want to free up a few hundred MB and don't need GUI apps, remove Gnome.  I'm to lazy to find the articles right now, but they're easy to find in the wiki.

---

