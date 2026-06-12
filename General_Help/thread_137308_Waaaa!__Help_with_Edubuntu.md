---
title: "Waaaa!  Help with Edubuntu"
date: 2006-02-27
forum: General Help
---

### Post by loninappleton on 2006-02-27
Little lonnie, age 57 has a problem with Edubuntu.


In my efforts to learn Edubuntu enough to recommend it
to a mom with a 9 year old, I made an install of Edubuntu 5.10.

I have one user and root.

Well, in playing around, I deleted the 'panel' where all the applications, places etc are tabbed.


How do I get these back?  I should not have to reinstall
for something so simple.

Also can I go into root and fix/find my dsl net connection?
I don't seem to be getting out using Firefox...  Firefox disappeared from the desktop too.


I'm looking forward to the Dapper release and want to 
get these kids going on Linux.  Buit I am not an experienced user of Linux myself much either.


I can get to the root and user directories and that's about it.


Will there be tutorial materials for Edubuntu that can be 
printed out?


Can I get an email notification for the release of the 
Edubuntu Dapper Live cd?  Live Cd from 5.10 that I 
burned as an ISO had problems:  the tabs for the 
applications, places etc would not _stay open_.  I hope that problem got solved for Dapper.


Thanks for the help

---

### Post by mlind on 2006-02-27
Hi, 

you can revert to default desktop look by deleting user defined settings
which reside below your home directory.

If you use Gnome as a Desktop environment, these directories are named
.gnome and .gnome2 (for kde I guess it's .kde) 

if your username that you login on ubuntu is 'loni'
by deleting /home/loni/.gnome2/ and its contents should revert you back to defaults.
You need to logout and login after this.

Please make backups before doing this!!

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
contains short but useful documentation and simple tutorials

---

### Post by loninappleton on 2006-02-27
I don't see how to do this except in root.

Unless I can login lon, pwd, then get to a terminal screen (?)

---

### Post by taurus on 2006-02-27
You don't have to be root to remove stuff in your account.  Try this

```

rm -rf ~/.gnome ~/.gnome2

```

---

### Post by mlind on 2006-02-27
[QUOTE=loninappleton]I don't see how to do this except in root.

Unless I can login lon, pwd, then get to a terminal screen (?)[/QUOTE]

Rule of thumb is that you should prefer 'sudo' instead of root account
(I guess ubuntu already does this in a way by hiding root password)
and don't use sudo/root commands on your home folder files unless
you absolutely know what you're doing.

I try to avoid sudo as much as possible. Things break seldom that way.  And I'm
forced to use sudo if I need root privileges. Writing that sudo command in front of
everything may seem irritating, but atleast it makes you think what you're doing,
and accidents will happen seldom too.

In Windows, it's easy to break whole system by accidentally drag-and-drop some
system folder into wrong place. Scary stuff.


You can open gnome-terminal by invoking *Alt+F2* keys and writing
*gnome-terminal* on command prompt. Or you could use one of the virtual terminals
by doing *Ctrl+Alt+F1*.  *Ctrl+Alt+F7* will get you back on Gnome (X-terminal). 

Then do as taurus said.

---

### Post by loninappleton on 2006-02-27
And then promptly lock the desktop so it doesn't happen again.


I'll try what you both said.

Especially in a prog like Edubuntu, I wonder why there's
so little error handling-- as in the manner of "Are you sure you want to make all the prompts diappear on the desktop?"  After all, a kid is going to be using this.


I'll be back with whatever error message I get from doing the control key procedures mentioned above.  I've been down this road before.

---

### Post by loninappleton on 2006-02-28
Ok,


   The code i got yesterday went in with no errors.

The bad news is it didn't change the desktyop and put
back all the tabs across the top.  I reinstalled which
took longer than i thought it would, but it was late at
night.

  If a a panel can be deleted so easily, then why isn't there
like a check box to turn it back on?  I know that when I ask these questions, the regulars think I'm a troll.  I'm not,  I really want to know.

  Since this is an Edubuntu thread, I want to ask also how to set up my DSL.   I believe I have an error in the IP
address and would be looking for the standard boxes to fill in my name, domain and such to get the DSL
working. If I'm setting up an Edubuntu from scratch, should not the init routine find my Linksys card and
Actiontec modem/router?


  I've found the tab to the terminal, can I use pppoe from there or use the Network config utility?


  These might be all specific to Edubuntu.  My most recent experices were with KDE rather than Gnome.

---

### Post by dbott67 on 2006-02-28
[QUOTE=loninappleton]If a a panel can be deleted so easily, then why isn't there
like a check box to turn it back on?  I know that when I ask these questions, the regulars think I'm a troll.  I'm not,  I really want to know.[/QUOTE]

To add/remove from the panel (or create new ones), right-click on a blank space  & select "add to panel".  Drag & drop any items onto the panel.  The applications/places/system menu is highlighted in my screenshot (it's called "Menu Bar").  You'll notice that I have 3 panels... top, bottom and side, and have added a second "menu bar" to the side panel.

I remember the first time I nuked a panel item, too.  Cried myself to sleep for 2 days until I figured it out! :)

Hope this helps.

---

### Post by loninappleton on 2006-02-28
Hello,

  I recall seeing some panel info like that but not how to
retrieve the whole panel.. an UNDO command as one 
might find before logging out of a sound editing program
for instance.

  There was one other option that popped up and showed a button to return to default-- but it didn't.


  I read in the Linux mag that a new Gnome and a new KDE main release are both due soon.  Will they address this at all?


   Yes, an 'undo'.  That is what is called for to prevent those long sleepless and tear-filled nights.


;-)

lon

---

### Post by dbott67 on 2006-02-28
[QUOTE=loninappleton]I read in the Linux mag that a new Gnome and a new KDE main release are both due soon.  Will they address this at all?

   Yes, an 'undo'.  That is what is called for to prevent those long sleepless and tear-filled nights.

;-)

lon[/QUOTE]

No idea if they will address this in Gnome 2.14 (TBR March 15).  Ubuntu developers generally plan to release a new version of Ubuntu to incorporate the latest version of Gnome.  In this case the next version of Ubuntu (6.04 aka Dapper) is scheduled for release in April.

A few weeks ago I went to [www.gnome.org](www.gnome.org) to find out what improvements & additions they made to 2.14, but I don't recall seeing anything about adding this as a feature.

-Dave

---

### Post by loninappleton on 2006-02-28
I think to put it another way that it is more important for
the Edubuntu developers to address this issue-- the ability to quickly "start over" than may be necessary for the 
general Ubuntu community.  In various distros there's
the ability to 'save current setup' or discard and reload.

This seems to be unclear or unavailable in Edubuntu/Gnome desktop.  I'm sure it can be addressed.

---

