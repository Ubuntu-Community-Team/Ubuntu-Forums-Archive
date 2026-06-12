---
title: "Flash stopped working in 64 bit Hardy"
date: 2010-01-15
forum: General Help
---

### Post by pricetech on 2010-01-15
I know 64 bit Flash has been a headache, but mine was working until yesterday.  Symptoms began with it not working in Opera and Seamonkey.  I checked the Adobe site and found what appears to be a later version, so I downloaded it, extracted it, then copied it to the relevant directories.  That changed nothing at the time, but this morning it stopped working in Firefox as well.

Anybody else having this issue ??  Any ideas ??  Thanks in advance.

---

### Post by pricetech on 2010-01-18
Bump, and:

From what I'm seeing in other posts I may be dealing with old information.

I have libflashplayer.so copied to:
/usr/lib/mozilla/plugins
/usr/lib/opera/plugins
/home/username/.mozilla/plugins

Is there an additional location that I'm not aware of ??

Is there now an installer for the 64 bit plugin or is there a workaround that has recently come about ??

Again, everything was working just fine until Thursday when flash stopped working in Opera and Seamonkey, then it stopped in Firefox Friday morning.

---

### Post by oldos2er on 2010-01-18
There's a script here: [http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html)

---

### Post by pricetech on 2010-01-19
> **oldos2er said:**
> There's a script here: [http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html)

Didn't work.  I didn't actually use the script since he's pointing to an older version of flash, plus I don't have all the directories he lists, but I did copy libflashplayer.so to /usr/lib/seamonkey/plugins/ as well as /usr/lib/xulrunner_addons/plugins with no joy.

(sigh)

---

### Post by oldos2er on 2010-01-19
You can edit the flash version. I don't know much about Seamonkey, but if you have /usr/lib/mozilla/plugins, I'd copy libflashplayer.so there if you haven't already.

---

### Post by pricetech on 2010-01-19
Yep, it's already there.  I downloaded again from Adobe and replaced it just in case.

Still no joy.

---

### Post by nanotube on 2010-01-19
does it show up in about:plugins?

are you not by any chance mixing a 64bit browser + 32bit plugin, or 32bit browser + 64bit plugin (which won't work - the architecture of browser + plugin has to match) ?

---

### Post by pricetech on 2010-01-19
I have it working again.  I downloaded again from Adobe Labs and copied it to all the relevant locations.  After that, it works in Firefox, Opera, Seamonkey.

Here's my updated "note to self" in case it might help someone else:

Download the 64 bit Flash Player from Adobe Labs.  I suggest you go here:
[http://labs.adobe.com/](http://labs.adobe.com/)
and look for the latest flash listed under Recent Releases since it seems to be a moving target.

Extract the archive and copy libflashplayer.so to the following locations:  NOTE: They may not all exist on your particular installation.
/usr/lib/firefox/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/mozilla/plugins
/usr/lib/opera/plugins
/usr/lib/seamonkey/plugins
/usr/lib/xulrunner-addons/plugins
/home/username/.mozilla/plugins

I got an error on /usr/lib/firefox/plugins because I don't have that directory, but everywhere else went happily.

Hope this helps someone else.

---

### Post by pricetech on 2010-01-19
> **nanotube said:**
> does it show up in about:plugins?

are you not by any chance mixing a 64bit browser + 32bit plugin, or 32bit browser + 64bit plugin (which won't work - the architecture of browser + plugin has to match) ?

I checked about plugins in firefox and it showed up.

I'm not mixing architecture, unless I somehow grabbed a 32 bit flash from the 64 bit page.

---

