---
title: "firefox, buttons not working"
date: 2009-08-27
forum: General Help
---

### Post by bender1234 on 2009-08-27
Hey.

Have anyone experienced that the buttons in firefox simply stops working?

Have this odd error which came out of nowhere, all buttons have suddenly stopped working. (no plugins or anything have been installed, it just came out of the blue)

bender

---

### Post by nikhilbhardwaj on 2009-08-27
you should remove the .mozilla directory in your home directory
and run firefox again
that should solve it
you may back up your profile if you need something from it
close firefox and then
```

cd ~
mv .mozilla mozilla-profile-backup

```
now start firefox
this way you can restore your profile or bookmarks or whatever you need

---

### Post by bender1234 on 2009-08-28
Hi thanks for your response.

For some odd reason it all started working again.

Btw are you supposed to install plugins in home/.mozilla/plugins?
Or should they all be in /usr/lib/mozilla/plugins (guess the first dir only installs it for that user only).
Also what is this dir for /usr/lib/firefox-addons/plugins?
I mean why do you have both the mozilla and the firefox dir?

regards,
Bender

---

