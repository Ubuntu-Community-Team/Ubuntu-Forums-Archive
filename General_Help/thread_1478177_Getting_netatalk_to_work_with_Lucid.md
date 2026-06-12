---
title: "Getting netatalk to work with Lucid"
date: 2010-05-09
forum: General Help
---

### Post by zim2dive on 2010-05-09
EDIT: I jumped the gun.. still having troubles.. here's the current work in progress

I had a nicely working netatalk setup with Karmic (which broke after the Lucid upgrade)

To pre-empt a sure set of suggestions: No, I am NOT interested in accomplishing this with samba.

Ok, back on topic...

I'm 50% of the way there.. I think

Steps:

- sudo apt-get install libdb46-dev (so that you get the header file too)
- then download netatalk 2.1 from [https://sourceforge.net/projects/netatalk/files/](https://sourceforge.net/projects/netatalk/files/) .. unpack and run "./configure --enable-debian"

at this point I had an install into /usr/local/etc/netatalk

Looking at my previous afpd.conf and AppleVolumes.Default files, I copied over the folders I wanted shared, ie. ```
~/ HomeDir cnidscheme:tdb
/media media cnidscheme:tdb
```

NOTE: I used to have an "allow" string.. I removed that b/c I could not get it to work.  I could open the top folder, but none of its sub-folders.

I then ran "sudo afppasswd -c" and then sudo afppasswd -a USER" to create user USER

I found I had to add uam methods and password file pointer in afpd.conf```
 -passwdfile /usr/local/etc/netatalk/afppasswd
-uamlist uams_guest.so,uams_clrtxt.so,uams_dhx.so
```

and did a "/etc/init.d/netatalk restart"

I think this was all the steps.

Still working out bugs tho.

---

