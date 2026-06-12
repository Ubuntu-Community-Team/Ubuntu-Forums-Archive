---
title: "NX server uninstall problem"
date: 2010-08-30
forum: General Help
---

### Post by coolgenes on 2010-08-30
Hi all, I had a friend help me install freenx ~6 mos. ago.  It stopped working and I got tired of trying to fix it, though I would uninstall and reinstall instead, sounded like a good idea at the time anyway.  Now I have an error that it wasn't uninstalled completely and I don't understand what needs purged so I can complete a reinstall.  Can anyone help with this?  I am running Ubutu 10.04 but it was installed on the previous version (Karmic), on an AMD 64 bit system.  Any help in decyphering this error code and suggestions on what to do next would be appreciated.
Keep in mind, this was during the UNinstall, why is it wanting to add users during the UNinstall?  also FYI I did the package Uninstall from Synaptic searching for NX and found the main package to uninstall that way.

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
Setting up nxserver (3.4.0-14) ...
NX> 704 ERROR: Cannot add user: nx.
NX> 704 ERROR: User: nx already exists.
NX> 704 To fix the problem, you may try to completely uninstall NX
NX> 704 Server and install it from scratch. If this is not enough,
NX> 704 please delete the nx user by using the system commands and
NX> 704 proceed with a new installation of NX Server.
dpkg: error processing nxserver (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by coolgenes on 2010-08-31
bump :)

---

### Post by jerome1232 on 2010-08-31
Looks like the user was not removed in the previous removal, so I would just manually remove that user, just to be thorough and cautious at the same time tell it to remove all files owned by nx and backup all of those files before removing them.

From more info abut the deluser command or if you want to get a good look at what I'm suggesting you to do check out the man page for deluser!

change the bit about --backup-to to a real folder on your system. It's where the backup will go to.
```
sudo deluser --backup-to /place/to/backup/users/files --remove-all-files nx
```

---

### Post by coolgenes on 2010-09-01
I'm confused about this user.  If I open up my users info there is no user there, there was an nx group though, but I deleted this when I saw the error.  Is this user visible?

---

### Post by jerome1232 on 2010-09-02
It's probably a system user which to my knowledge won't show in the users and groups gui.

If the following code returns a line with nx then the user exists and you probably just need to manually delete it.

In case your worried the following command will not show any users passwords, they are in a different file (/etc/shadow if I remember right)  and encrypted. I believe that file is only readable by root as well.
```
cat /etc/passwd | grep nx
```

---

### Post by coolgenes on 2010-09-02
OK, I tried two things
$ sudo nxserver --userlist
sudo: nxserver: command not found

-so not sure why this didn't work, so then I saw your post jerome and this is what I got

~$ sudo cat /etc/passwd | grep nx
nx:x:118:128:FreeNX Server,,,:/var/lib/nxserver/home/:/usr/bin/nxserver

-so can I just go into /var/lib/nxserver/home/ and /usr/bin/nxserver and delete those directories with rm -r?

---

### Post by jerome1232 on 2010-09-02
You didn't need to run the command as root, doesn't matter really but it's a good habit to only use sudo when you need it, and to learn when you need it and when you don't.

Did you try the deluser command I gave in my first post?

---

### Post by coolgenes on 2010-09-03
It hung in the terminal.  I let it go for 2 hours and nothing so I canceled it.  I can try again and let it go overnight?

---

### Post by jerome1232 on 2010-09-03
Well you could try leaveing out the backup-to switch (maybe that's what stalled it)

---

### Post by coolgenes on 2010-09-04
had it run overnight.  Need to find time to go back into work to look at it.  this is why I need NX :)  I'll post an update as soon as I manage to make it in.

---

### Post by coolgenes on 2010-09-07
yes, it finished and it says it was successful.  I tried reinstalling freenx, client node then server.  bad idea. still doesn't seem to work.  What is your recommended next step?

---

### Post by coolgenes on 2010-09-09
finally tried a reinstall of the nxclient (no errors reported), nxnode (no errors reported), and nx server, error posted:


NX> 701 Checking NX server configuration using /usr/NX/etc/server.cfg file.
NX> 701 ERROR: Output: chown: invalid user: `nx:root'.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc' to 'nx:root'.
dpkg: error processing nxserver (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver


Is there any way to fix this problem?  I'm not sure how to change the ownership of the user.  and should the /usr/NX/etc dir be only shared by nx:root?

will I need to reinstall nxserver once I change the permissions or is the rest of the program already installed?

Thanks

---

### Post by coolgenes on 2010-09-10
Anyone know how to fix this or where a faq for nx nomachine server is?

---

### Post by coolgenes on 2010-09-13
If anyone is interested I used jerome's suggestion on deleting the nx user which took care of the one problem.  I had to use a combination of synaptic package manager and downloads from the nomachine website but finally got it installed and working.

---

### Post by jerome1232 on 2010-09-13
Glad you got it working!

---

