---
title: "Ubuntu won't suspend automatically any more"
date: 2012-07-21
forum: General Help
---

### Post by sparhawkthesecond on 2012-07-21
Hi,

In the last few weeks, Ubuntu has stopped sleeping automatically. I've gone to System Settings > Power, and verified (and toggled) "suspend on inactive for" to 5 minutes (for both battery and "when plugged in"), but the system stays awake.

Also , I've used code similar to
```
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 300
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 300
```to set the timeout values. I've also verified these in dconf  Editor. Previously, I could set this quite low to make my computer sleep quickly, but now it no longer works either.

I'm not sure if this is relevant, but under old versions of Ubuntu, if I wanted my computer to never suspend (via the CLI), I would also set
```
$ gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac false
```At some point, this seemed to have been depreciated (and also gives me the error "No such key 'sleep-inactive-ac'"). I found that it it was enough to set sleep-inactive-ac-timeout to 0. This worked for a while, but at some point auto-suspend stopped working. Oddly enough, the sleep-inactive-ac key is still present when I look via dconf editor. However, when I click it, it says "no schema", and the summary, etc. fields are blank.

I'm also not sure if this is relevant, but I've uninstalled gnome-screensaver, and installed xscreensaver. I have tried killing xscreensaver and re-installing gnome-screensaver, but this did not help.

Also, I've tried setting sleep-display-ac to 4 seconds via dconf editor, but this had no effect either.

---

### Post by sparhawkthesecond on 2012-08-02
Desperation bump!

---

### Post by sparhawkthesecond on 2012-08-10
I've attempted more troubleshooting, by creating a new user account,  then logging out of the main account and into the new account. I've  tried modifying the timeouts via dconf, but get the same results as  above (i.e. it doesn't work, nor does sleep-display-ac, but  idle-dim-time and idle-dim-ac work). Also, the depreciated  sleep-display-ac key is not visible, so I think that this is probably  unrelated.

---

### Post by sparhawkthesecond on 2012-08-18
This is driving me crazy. Can someone please help? Perhaps someone could at least show me how to reset everything to the default values?

Anyway, I've got some new information and I've attempted to troubleshoot some more.

I've also noticed some trouble with DPMS. I'm not sure if this is related, but I'll put the information here, just in case. Using xscreensaver, I set Power Management to enabled, with standby and suspend timeouts to 10 minutes. I've verified these settings in ~/.xscreensaver and xset q. However, the screen blanks after about 30 seconds. If I turn off DPMS (either via xscreensaver GUI or modifying ~/.xscreensaver), it won't blank at all, so I know that DPMS is partially reading the xscreensaver settings.

I also attempted to restart and log into the new account immediately, just in case my main account was "poisoning" the system. Automatic suspend still fails, but oddly enough, sleep-display-ac now works, and respects the values that I put in it.

---

### Post by sparhawkthesecond on 2012-09-02
Another bump. :sad:

Surely someone knows how to reset the suspend values to default?

---

### Post by sparhawkthesecond on 2012-09-23
I've since moved to gnome-shell instead of unity, and still have this  problem, so I guess that it's something to do with gnome-power-manager.

---

### Post by sparhawkthesecond on 2012-09-24
If anyone ever reads this thread, [this]("http://askubuntu.com/a/180505/53508") fixed it for me.

---

