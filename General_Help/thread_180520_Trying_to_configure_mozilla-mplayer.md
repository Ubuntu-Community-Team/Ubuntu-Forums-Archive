---
title: "Trying to configure mozilla-mplayer"
date: 2006-05-22
forum: General Help
---

### Post by Fafnir on 2006-05-22
AAARRRRGGGHH!!!!! (Five exclamation marks - the sure sign of a damaged mind...)

Here's my situation: I've been trying to configure the MPlayer plugin for Firefox (I'm using mozilla-mplayer 3.05-1, Firefox 1.0.8-0 and mplayer-386 1:1.0-pre7cvs, installed with Synaptic) to ignore audio files and not start playing automatically. For its part, Firefox has been trying (with considerable success) to stop me. FYI, I know a fair amount about computers in general, but I'm pretty new to Linux.

There don't seem to be any ways of changing that from the GUI (right-click->Configuration from within the plugin doesn't have the requisite options, and I don't know of any other way of getting at the options), so I've been looking at the conf files.

From what I've read (and from the requisite .conffiles file in /var/lib/dpkg/info), the relevant file is /etc/mplayerplug-in.conf. I think I've found the right changes to make, too - I've added #autostart=0 and #enable-mp3=0, and changed #enable-ogg=1 to #enable-ogg = 0. #use-mimetypes is set to 0, so it should be taking the file types from mplayerplug-in.conf instead of mplayerplug-in.types. 

My basic problem is that no matter what I do, Firefox refuses to recognise my changes in the conf file! I've checked [the official site]("http://mplayerplug-in.sourceforge.net/config.php"), and I've tried deleting $HOME/.mozilla/pluginreg.dat and/or touching mplayerplug-in.so as it suggests, then restarting Firefox, but to avail. I've done it every time I've made a change.

I doubt that's the problem anyway, though, since Firefox is ignoring the change to the autostart variable as well as the MIME types. I know I'm touching the right mplayerplug-in.so (there are multiple copies scattered around by the installer - I'm touching the one in /usr/lib/mozilla/plugins), since I went into about:config and set plugin.expose_full_path - and Firefox displayed that one under the filename field in about:plugins.

I've tried purging mozilla-mplayer, starting Firefox to be sure it recognises the plugin's gone (using about:plugins), closing it, reinstalling mozilla-mplayer, altering the conf file and THEN starting Firefox - in the hope that Firefox would check the conf file upon first detecting the plugin. No dice.

I knew this probably wasn't the problem since #use-mimetypes wasn't set in mplayerplug-ins.conf, but I tried editing mplayerplug-in.types and removing the undesired types by hand. That failed as well.

In a sort of last gasp, I tried hex editing mplayerplug-in.so. I found what looked like the plaintext MIME types, but after I edited it Firefox started dying when I tried to check about:plugins. I reinstalled and gave up on that type of attack.

My next course of action will probably be to uninstall mozilla-mplayer entirely, then try to build and install mplayerplug-in separately by hand (there's no package available). However, that's probably not a task for fainthearted, and I should *really* be revising for my A levels right now, so I've decided to beg for help before I try. (If I hadn't disabled smileys to get the boards to display "about:plugins" and "1.0.8-0" correctly, there would be a smiley here!)

Pretty please?

Thanks in advance!

---

### Post by nanotube on 2006-05-22
now, i use firefox 1.5, not 1.0.8, so this may be different, but on 1.5, you go Edit>Preferences>Downloads, click the "view and edit actions" button, and you can tell firefox what to do for any given filetype. very simple. 

i hope it is something similar in 1.0.8. if not... it seems it would be easier to upgrade to 1.5.0.3 than to do all the stuff you say you've done. :)

there is a great guide to upgrading firefox on the ubuntu wiki, here: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by Fafnir on 2006-05-22
[QUOTE=nanotube]now, i use firefox 1.5, not 1.0.8, so this may be different, but on 1.5, you go Edit>Preferences>Downloads, click the "view and edit actions" button, and you can tell firefox what to do for any given filetype. very simple. 

i hope it is something similar in 1.0.8. if not... it seems it would be easier to upgrade to 1.5.0.3 than to do all the stuff you say you've done. :)
[/QUOTE]

Oops... :oops: :-D

It's always the simple things! The dialog does exist in 1.0.8, and there is an option to enable or disable plugins for a given filetype... I knew about the dialog, but I always thought it was just for file associations upon downloading a file, not plugins! Thanks a lot!

Upgrading to 1.5 might well help Firefox identify the conf file itself, too (to disable autostart), since it's the latest version - good idea. I'll try that now...

---

