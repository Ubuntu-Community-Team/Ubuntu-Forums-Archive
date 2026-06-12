---
title: "Restart performs shutdown?!?"
date: 2010-04-02
forum: General Help
---

### Post by Arsaine on 2010-04-02
[SIZE=2][FONT=Verdana]Hello and I apologize if I'm posting this in the wrong place, but the nature of my problem confuses me so much that I don't know where to post this.

I've installed Karmic two weeks ago (before that I've been using Intrepid for a long time and had no similar issues). My system is Dell Inspiron 6400 notebook with 1 GB RAM and a Dual Core processor, mentioning this just in case it's needed. 

The problem: 'Restart' option from the Quit menu does not reboot the computer - it shuts down the system as if I chose the 'Shutdown' option. I have no idea why this happens or how to fix it. Reboot command from CLI works perfectly as it should, with all the parameters needed and without any "weird" output. You may be wondering why I'm so worried about this if I can perform reboot normally from command line - while that *is* true, I would really like to know how to fix this, or perhaps it is more important/interesting to find out what caused this unusual problem.

P. S. Suspend and Hibernate work normally.

Thank you all in advance.

~Arsaine
[/FONT][/SIZE]

---

### Post by garvinrick4 on 2010-04-02
See what this Does Code:

sudo shutdown -r now

that should restart.

Then open configuration editor and go Apps to indicator-session and check the second
box. Leave the first box unchecked.

If not installed is 

sudo apt-get install gconf-editor

Comes up in System Tools.

---

### Post by Arsaine on 2010-04-02
> **garvinrick4 said:**
> See what this Does Code:

sudo shutdown -r now

that should restart.

Then open configuration editor and go Apps to indicator-session and check the second
box. Leave the first box unchecked.

If not installed is 

sudo apt-get install gconf-editor

Comes up in System Tools.

The command works (I've tried it before), but in gconf editor there are no entries under indicator-session. No names, no values, nothing. :(

---

### Post by garvinrick4 on 2010-04-02
> **Arsaine said:**
> The command works (I've tried it before), but in gconf editor there are no entries under indicator-session. No names, no values, nothing. :(
double click on it and in the window to the right will be 2 lines with places to check on or off. Under APPS to indicator-session and double click on indicator-session. 
Here is the version I have installed. If you have an earlier version Code:
sudo apt-get install --reinstall gconf-editor
that will upgrade.

rick@rick-laptop:~$ aptitude show gconf-editor
Package: gconf-editor
State: installed
Automatically installed: no
Version: 2.30.0-0ubuntu1
Priority: optional
Section: utils
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 3,465k
Depends: libc6 (>= 2.2.5), libdbus-glib-1-2 (>= 0.78), libgconf2-4 (>= 2.27.0),
         libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.20.0),
         liblaunchpad-integration1 (>= 0.1.17), libpango1.0-0 (>= 1.14.0),
         gconf2 (>= 2.10.1-2), gconf-defaults-service (>= 2.28),
         policykit-1-gnome
Description: An editor for the GConf configuration system
 GConf-Editor is a tool used for editing the GConf configuration database. This
 is not the recommended way of setting desktop preferences, but it might be
 useful when the proper configuration utility for some software provides no way
 of changing some option.

---

### Post by Arsaine on 2010-04-02
[IMG]http://i41.tinypic.com/maw9dz.jpg[/IMG]


This is how it looks like.
gconf-editor is version 2.28-0ubuntu1, I tried reinstall as you suggested but the same version got installed.
I don't know what to do :(

Could this be a hal-related problem??

---

### Post by garvinrick4 on 2010-04-02
Do a Code:

sudo apt-get clean (to clear out your old cache of programs)

Now do a code:

sudo apt-get install --reinstall gconf-editor

Now see if that goes out to repository and fetches a new upgrade.

---

### Post by Arsaine on 2010-04-02
> **garvinrick4 said:**
> Do a Code:

sudo apt-get clean (to clear out your old cache of programs)

Now do a code:

sudo apt-get install --reinstall gconf-editor

Now see if that goes out to repository and fetches a new upgrade.

Nope. Still the same version.
Sorry if I'm asking stupid questions, but how would that help? What's the indicator-session entry got to do with Quit menu and its commands? I don't really understand what controls that menu or if it's possible at all to edit it. :/

---

### Post by garvinrick4 on 2010-04-02
Opened a karmic install and had 2.28 installed of gconf-editor and in Apps to indicator-session
had one box to check. suppress_logout_restart_shutdown.
 I have it checked so as not to wait 60 seconds to restart of shutdown.

Why when I double click on indicator-session and you do not I do not know. Hopefully
remove and install with clean cache will get a fresh copy that works properly.

---

### Post by garvinrick4 on 2010-04-02
> **Arsaine said:**
> Nope. Still the same version.
Sorry if I'm asking stupid questions, but how would that help? What's the indicator-session entry got to do with Quit menu and its commands? I don't really understand what controls that menu or if it's possible at all to edit it. :/
It controls the restart and shutdown in GUI (desktop).  Trying to see if they are checked you
will get the proper reaction from your dropdown menu to restart and shutdown.

When you did it from command line it worked properly sudo shutdown -r now for restart and
sudo shutdown -h now for shutdown. So it has to be in the GUI settings.

---

### Post by Arsaine on 2010-04-02
> **garvinrick4 said:**
> It controls the restart and shutdown in GUI (desktop).  Trying to see if they are checked you
will get the proper reaction from your dropdown menu to restart and shutdown.

When you did it from command line it worked properly sudo shutdown -r now for restart and
sudo shutdown -h now for shutdown. So it has to be in the GUI settings.

Okay, thank you. I'll try to find the package for the new version and install it, maybe this will work.

---

### Post by Arsaine on 2010-04-02
I checked in Synaptic and I don't have indicator-session package installed at all. Don't know why. Should I install it??

---

### Post by garvinrick4 on 2010-04-02
> **Arsaine said:**
> I checked in Synaptic and I don't have indicator-session package installed at all. Don't know why. Should I install it??
Yes, mine is installed.

---

### Post by getglenn on 2010-09-04
i too have this problem, but it has only started recently [maybe after an update?] and i can find no solution...

am running lucid

---

