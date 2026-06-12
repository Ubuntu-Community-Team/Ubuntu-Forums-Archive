---
title: "unity loses settings on restart"
date: 2011-05-03
forum: General Help
---

### Post by truant on 2011-05-03
Every time I load unity - either by rebooting, logging out/in, or just "unity --replace" all my self-placed launchers are gone (just chrome, terminal and a custom launcher for my email) and the LibreOffice ones are back.

I'm assuming this isn't a bug, as here and launchpad would have tonnes of reports of something so obvious if it were affecting everyone, but something local to me. Anyone know where I should start looking?

---

### Post by Shmantiv_Radio on 2011-05-03
> **truant said:**
> Every time I load unity - either by rebooting, logging out/in, or just "unity --replace" all my self-placed launchers are gone (just chrome, terminal and a custom launcher for my email) and the LibreOffice ones are back.

I'm assuming this isn't a bug, as here and launchpad would have tonnes of reports of something so obvious if it were affecting everyone, but something local to me. Anyone know where I should start looking?

Did you upgrade or fresh install?

---

### Post by truant on 2011-05-03
Upgrade from an install of Maverick.

Edit: there are other settings that don't persist too - if I change the clock display (I like to have date up there too), that won't even appear, let alone stay around after a restart.

---

### Post by Shmantiv_Radio on 2011-05-03
> **truant said:**
> Upgrade from an install of Maverick.

Edit: there are other settings that don't persist too - if I change the clock display (I like to have date up there too), that won't even appear, let alone stay around after a restart.

Well upgrading in Ubuntu seems to cause nothing but problems for a lot of people. I would suggest you backup your data up to USB/DVD and do a fresh install. Sorry but it's just the least time consuming way to try to fix your issues.

---

### Post by truant on 2011-05-03
Thing is, it's not that un-time-consuming to reinstall/setup IDL and all the other slightly weirdy stuff I've got on this machine.

I should know better than to upgrade an Ubuntu system by now..  I bumped a Debian box all the way from Etch to Squeeze in one go the other day and it barely blinked.  Lesson there is release when it's ready, not when 6 months has passed from the last release.

Ho hum.  Thanks for the replies anyway, much appreciated.

---

### Post by truant on 2011-05-06
```
sudo apt-get install libdconf0
```

log out and back in again.

fixed.

Reinstall schmreinstall. :D

---

### Post by bralcan on 2011-07-29
> **truant said:**
> ```
sudo apt-get install libdconf0
```log out and back in again.

fixed.

Reinstall schmreinstall. :D

Thank you very much!
Works fine here, solved! :P

---

### Post by unadulterated on 2011-09-27
I was facing a similar problem, thanks just had to re-install the libdconf0.

---

### Post by chrarnold on 2012-02-16
I'd like to reopen this... I am also facing this very annoying issue, and none of the solutions here worked for me.

It does not matter if I select the gnome-session-fallback or the new Unity desktop,  changes in the panel are lost whenever I restart my laptop. The only thing that is kept is if I add symbols to the desktop, but any panel-related modifications are lost after I login again. Thus, I think something is really messed up in my system. I would appreciate any help for this issue, I cannot imagine I am the only one who faces this annoying problem?

Thanks,
Christian

---

### Post by aasdfasdfg on 2012-02-16
Can you give an example of the kinds of changes that are not persistent, both in the unity interface as well as in the fallback interface?

---

### Post by chrarnold on 2012-02-17
Hi, thanks for the reply, of course:

1) Unity (EDIT:  To avoid confusion, I mean the "Ubuntu" shell that one can select at startup)
If I add shortcuts (e.g., Thunderbird or a terminal) to the launcher at the left, they first stay there as I want, everything works as expected. However, after I login again, all the changes are lost. Additionally, if I delete shortcuts (e.g, Ubuntu One) from the launcher, they are back when I login again.

2) Gnome fallback
Here, I have two panels. One at the top and one at the bottom. They both forget the changes I made after I login again (shortcuts I add to the panel and items I add manually, like a window switcher for the bottom panel). If I add items to either one of the panels, everything seems to work fine at first, but after ... you know. I find it particularly annoying that the bottom panel has no items after I login, so hat I always have to add a window switcher in order to see all open windows.

Any ideas? I mean, shouldn't there be any warning or error messages either at the startup or when I make changes to the panels that indicate the source of the problem? 

When I do a "grep -i gnome syslog", I find the following entry:
gnome-session[27066]: WARNING: Application 'compiz.desktop' failed to register before timeout
gnome-session[27066]: CRITICAL: We failed, but the fail whale is dead. Sorry....

No sure if this is actually related to the problem, and the time stamp indicates thaht this is neither an event at the last shutdown nor when I last logged in, but maybe it is relevant?

EDIT2: Sorry for the edit, but I just installed the Cinnamon desktop and the same issue...It does not matter which GUI I use, they all have the same problem :(

Thanks!

---

### Post by aasdfasdfg on 2012-02-18
Can you post the full output of .xsession-errors?

---

### Post by chrarnold on 2012-02-19
Hi, a good suggestion. I looked in /var/logs before and didn't find an error message that is related to the problem, but .xsession-errors shows the following errors or warnings that cause the problems:

```

gnome-session[2008]: WARNING: Unable to find default provider 'notify-osd' of required provider 'notifications'
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
...
(metacity:2070): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"
...
GLib-GObject-WARNING **: gsignal.c:2295: signal `size_request' is invalid for instance `0x18ccbf0'
** Message: applet now removed from the notification area
** DEBUG: old state indicates that this was not a disconnect 0
** DEBUG: foo_client_state_changed_cb
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
...
GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
...

```It seems that the critical error is the "GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications." message. This seems to be a common bug that is not yet fixed, and I already tried various things to fix it, none of which worked:
1. dconf-tools and libdconf0, and dconf-gsettings-backend are installed, and removing and re-installing didn't help.

It seems that this is not trivial to fix and may require a full reinstall (see [https://bugs.launchpad.net/ubuntu/+source/dconf/+bug/915285](https://bugs.launchpad.net/ubuntu/+source/dconf/+bug/915285))

---

### Post by Querio on 2012-02-27
Same problem, seems bug #915285 says it all [settings lost on restart, cant change system settings like background or screen saver stuff, reinstalling libdconf0 did nothing].  All i did was update regularly, and blam, reinstall necessary.  Thanks for all the help, hope this bug gets fixed at some point.  For now I'll just revert to my LTS version.

---

