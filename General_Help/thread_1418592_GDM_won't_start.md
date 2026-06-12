---
title: "GDM won't start"
date: 2010-02-28
forum: General Help
---

### Post by flyver on 2010-02-28
So I'm giving Linux Mint 8 a try, and was ambitious enough to try installing a different GDM, specifically [this one]("http://gnome-look.org/content/show.php/Dust+Karmic+GDM+by+mickyz?content=107613").

I downloaded the file, but didn't do anything with it right away, since I noticed that I should (or maybe I shouldn't have?) inserted this command in "terminal":

sudo apt-get install gdm-2.20

Anyway, at some point I had a choice between choosing the current **something**, or using the publisher's **something**, but I could also select something else to get more information. I did that, and then I was unable to get out of it. _In the middle of the installation._

So I closed terminal.

After reboot, I have a white screen and some colours, but totally impossible to see any text.

Was able to get into the graphical environment and tried a couple of things after some googling, but the problem is still there.

Also, when shutting down, I only have the option to suspend or hibernate. Shut down and restart is greyed out.

Thank you for helping.

---

### Post by fooman on 2010-02-28
if you are able to get to a terminal....have you tried running that "sudo apt-get install gdm-2.20" command again,  this time choosing the "current **something**" option and letting that complete?

---

### Post by flyver on 2010-02-28
Yes I was able to get to a terminal. The first time I did that, it didn't work because something wasn't available because it already was open. Anyway, I did it again later and now it says that the latest version already is installed.

This is what shows up once I access a terminal and type startx:

*No servers were defined in the configuration file and XDMCP was disabled. This can only be a configuration error. GDM has started a single server for you. You should log in and fix the configuration. Note that automatic and timed logins are disabled now.*

---

### Post by flyver on 2010-03-01
I don't know what I did, but the standard GDM now starts. I am trying to configure the GDM2 configuration tool, but it doesn't work, only the standard Helena GDM appears...

Why so complicated. :?

---

