---
title: "Chromium/Chrome Lockdown, not working"
date: 2011-12-13
forum: General Help
---

### Post by inheritthewind on 2011-12-13
I'm trying to lock down some of the settings in Chromium/Chrome.
I've followed the instructions [[COLOR="Blue"]_here_[/COLOR]]("http://dev.chromium.org/administrators/linux-quick-start") and [[COLOR="Blue"]_here_[/COLOR]]("http://dev.chromium.org/administrators/policy-list-3").

I've created a config file [FONT="Courier New"]/etc/chromium-browser/policies/managed/test.json[/FONT] and pasted in a test setting:

[FONT="Courier New"]{
 "HomepageLocation": "ubuntuforums.org"
}[/FONT]

That looks like the correct syntax to me, but when I start Chromium, the settings aren't applied.

I tried installing Chrome, in case it was a problem with the Chromium package.  For Chrome the file has to be located in [FONT="Courier New"]/etc/opt/chrome/policies/managed/test.json[/FONT].
No difference.

Am I doing something wrong, or missing a step?

---

### Post by elvisd on 2011-12-13
Maybe file permission problems?
try setting it writable by admin only and readable by anyone

---

### Post by inheritthewind on 2011-12-13
Thanks for the reply.

The file permissions are exactly as you mentioned.  I think they're already set from above (the [FONT="Courier New"]/etc/chromium-browser/policies[/FONT] directory is created during the install).

I'd be interested if anyone has this working ....

---

### Post by inheritthewind on 2011-12-13
Quick update:

The lockdown file works with Chromium, on my openSUSE PC.
I just can't get it to work on either Ubuntu/Kubuntu PCs.

Can anyone else confirm it is broken - or is it just my installs?

---

### Post by inheritthewind on 2011-12-14
Do any chromium users have a couple of minutes to test this on their desktops?

I'm thinking it may need a bug report, but I've never submitted one before and I want to be 100% sure I'm not missing anything ...

---

