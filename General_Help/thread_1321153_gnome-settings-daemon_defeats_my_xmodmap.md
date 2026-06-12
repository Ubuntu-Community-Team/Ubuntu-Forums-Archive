---
title: "gnome-settings-daemon defeats my xmodmap"
date: 2009-11-09
forum: General Help
---

### Post by ajb2 on 2009-11-09
Hi, everyone,

Recently I posted a question complaining about inconsistent behavior involving XDMCP.  I'm trying to get a user with a
rather old NCD X terminal to be able to log into an Ubuntu system via XDMCP, and it hasn't been working consistently.  The biggest problem is that the keymap is wrong about 60-70% of the time when I bring up a Terminal window; I've also had less frequent problems with fonts being wrong and some display elements being fuzzy.

I've been able to track down the keymap problem further.  There is an .Xmodmap in the home directory.  It appears that during the login process, xmodmap is called twice.  The first time, it's called with the command

/usr/bin/xmodmap <home>/.Xmodmap

from the /etc/gdm/Xsession script, which is what I expect.  However, at some point, xmodmap is later run again, with this command:

sh -c xmodmap /usr/share/xmodmap/xmodmap.us

run by gnome-settings-daemon.  This keymap is wrong for the X terminal, and causes the keys to misbehave.

I don't yet know how xmodmap is called those times when the keymap works; i.e. I don't know whether gnome-settings-daemon isn't running xmodmap at all, or whether it happens to run it before the command is run from Xsession.

I haven't found much info on gnome-settings-daemon, so I don't know what it's for, how it works, or whether there are config items that control its operation.  I think there's a fair chance that the keymap problem is related to the other inconsistency problems I'm seeing---i.e. it's related to gnome-settings-daemon screwing something up if it happens to perform a command at the wrong time.

Any insights?  Thanks in advance.

---

### Post by ajb2 on 2009-11-11
FYI, after Googling around a bit, I'm forming an impression that gnome-settings-daemon just may not work right if the X server doesn't support the RANDR extension---and the NCD X terminal my user is using (which I think was from about 1994) doesn't support this.  Maybe there's a way to get gnome to work without it, but at this point we've agreed that there's little value in working on this further, and that we just need to upgrade the user's technology.

Thanks anyway.

---

