---
title: "embedded real player in konqueror"
date: 2006-04-25
forum: General Help
---

### Post by uwo on 2006-04-25
can't get the real player to embed in konqueror.

real player installed and works in firefox and epiphany (embedded), in konqueror not.

will paste from about:plugins, as there are some "not founds" which might be the problem:

> 
Helix DNA Plugin%3A RealPlayer G2 Plug-In Compatible  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.581 built with gcc 3.2.0 on Feb 1 2006  nphelix.so
  audio/x-pn-realaudio-plugin - RealPlayer Plugin Metafile (rpm)

MozPlugger 1.7.1  MozPlugger version 1.7.1, written by Fredrik Hübinette <hubbe@hubbe.net> and Louis Bavoil <louis@bavoil.net>.
For documentation on how to configure mozplugger, check the man page. (type man mozplugger) 
Configuration file:  Not found!
  Helper binary:  Not found!
  Controller binary:  Not found!

  mozplugger.so

Does anybody know, what could be wrong? I would love to use konqueror for all surfing and not have to go to firefox for a certain page i use daily.

(the sight i need this for is [www.rtvslo.si](www.rtvslo.si), link Avdio/video in top panel)

thanks.

---

### Post by uwo on 2006-04-26
additional info. same quote from firefox about : plugins seems better:

> 
    File name: mozplugger.so
    MozPlugger version 1.7.1, written by Fredrik Hübinette <hubbe@hubbe.net> and Louis Bavoil <louis@bavoil.net>.
    For documentation on how to configure mozplugger, check the man page. (type man mozplugger)
    Configuration file:	/etc/mozpluggerrc
    Helper binary:	mozplugger-helper
    Controller binary:	mozplugger-controller

nevertheless I have the mozilla-firefox/plugins directory as the directory to search for plugins in konqueror - same plugin then listed as installed, however withoug configuration, helper and controller files and binaries.

---

### Post by raydar on 2007-10-31
Same problem here, only I got to it by trying to play Flash in Konqueror.

Firefox about:plugins reads

Configuration file:	/etc/mozpluggerrc
Helper binary:	mozplugger-helper
Controller binary:	mozplugger-controller

Konqueror about:plugins reads

Configuration file:  Not found!
  Helper binary:  Not found!
  Controller binary:  Not found!

Both mozplugger and konqueror-nsplugins are installed, and I reinstalled the latter just for good measure, thinking maybe the sequence those are installed in had something to do with it, but no dice.  

I then tried rooting around for a Konqueror config file to edit, with the hope of just putting in "/etc/mozpluggerrc" and "mozplugger-helper" and "mozplugger-controller" in the appropriate blanks.  But I couldn't find any files that had "Configuration file" and "Helper binary" and "Controller binary" fields in them.

I'd like to try using Konqueror exclusively as the web+file browser it's supposed to be, but it's gotta play everything I can play in Firefox in order for that to be feasible.

EDIT: Haha look what it did to the colons!

---

### Post by erythrocyte on 2008-04-29
Hi there! I filed a bug about this at [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/217108](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/217108) . Any howto on resolving this would be greatly appreciated. Is there a way to use another player (mplayer, kmplayer, kaffeine, etc.) instead?

---

### Post by erythrocyte on 2008-04-29
> **raydar said:**
> Same problem here, only I got to it by trying to play Flash in Konqueror.

Firefox about:plugins reads

Configuration file:	/etc/mozpluggerrc
Helper binary:	mozplugger-helper
Controller binary:	mozplugger-controller

Konqueror about:plugins reads

Configuration file:  Not found!
  Helper binary:  Not found!
  Controller binary:  Not found!

Both mozplugger and konqueror-nsplugins are installed, and I reinstalled the latter just for good measure, thinking maybe the sequence those are installed in had something to do with it, but no dice.  

I then tried rooting around for a Konqueror config file to edit, with the hope of just putting in "/etc/mozpluggerrc" and "mozplugger-helper" and "mozplugger-controller" in the appropriate blanks.  But I couldn't find any files that had "Configuration file" and "Helper binary" and "Controller binary" fields in them.

I'd like to try using Konqueror exclusively as the web+file browser it's supposed to be, but it's gotta play everything I can play in Firefox in order for that to be feasible.

EDIT: Haha look what it did to the colons!
@raydar -

Konqueror 3.5.8 has a known issue with Adobe's flash plugin. Konqueror 3.5.9, which  comes with KDE 3.5.9 in Hardy, handles flash much better.

EDIT: Darn. Flash in Konqueror 3.5.9 is unreliable too. Sometimes it works flawlessly. Other times all I get are grey boxes.

---

### Post by erythrocyte on 2008-04-29
I've managed to use KMPlayer to play embedded Real Player media in Konqueror. A howto that describes it can be found here:-

[http://mydominanthemisphere.wordpress.com/2008/04/29/howto-play-embedded-real-player-media-in-konqueror-using-kmplayer/](http://mydominanthemisphere.wordpress.com/2008/04/29/howto-play-embedded-real-player-media-in-konqueror-using-kmplayer/)

---

