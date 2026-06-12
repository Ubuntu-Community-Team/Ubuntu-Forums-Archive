---
title: "An Ubuntu rant about Thunderbird 8"
date: 2011-11-28
forum: General Help
---

### Post by giowck on 2011-11-28
Hi,

I recently updated Thunderbird ( from 7 to version 8 ), and lost all my calendars.

I was using the Lightning extension installed through th software center.

After today's update, I lost all settings related to Lightning.
All local calendars and my Google Calendar were lost in the nirvana.

How the hell could this happen?? Just by an automatic update?
Note: I found that the lightning extension was removed by the upgrade, so after installing it again through USC, just started Thunderbird 8 and boom! All data has been erased.

Why did the update remove the lightning extension? WHy not just upgrade it too???

Damn! I'm so angry.
I can't work this way. That must not be.

Sorry for this rant, but I had to!

---

### Post by ajgreeny on 2011-11-28
When I upgraded my TB to v8, as you have done, I was offered the chance to update the lightning add-on.  I wonder why you were not given that option.

How did you install lightning in the first place?  I used the mozilla add-on site to find it and download it, and then installed it in TB from the Tools menu, if I remember correctly.  Did you install from the ubuntu repos?

---

### Post by Habitual on 2011-11-28
Several notes on numerous versions [here]("https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/") say "Works with Thunderbird 8"

---

### Post by Frogs Hair on 2011-11-28
I too was offered the option to update the calendar . As far as extensions are concerned it is up to the developer to update them for the latest version of Firefox or Thunderbird .

---

### Post by giowck on 2011-11-28
Thanks God on my laptop my calendars are still intact. (and of course did a backup befoere updating)

So now I'm facing these bugs:
[https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/897156](https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/897156)

and

[https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/897153](https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/897153)

Same as every Thunderbird update, this happened also for the 7 series xD

Hey packagers need some help??? I'm willing to do that for you! :P

---

### Post by Bobhuber on 2011-11-28
The lightning time zone extension (xul) was broken by using the package installer. I found a bug report already posted on it. To fix the problem this is what I did. Uninstall  "xul-ext-calander-timezones" and "xul-ext-gdata-provider"  using the synaptic package manager. Download the updated deb from here
 [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/2952789](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa/+build/2952789)
and install it using the gdebi package installer (not the software manager). It will tell you that the same  package version already  exists but ignore it and install from the downloaded deb. Go back into the package manager and reinstall the "xul-ext-gdata-provider". This fixed everything for me without losing any of the calendar data.and I hope it helps you.

---

### Post by giowck on 2011-11-28
thank you a lot.

I'll install these packages manually.

---

### Post by kurt18947 on 2011-11-28
I updated this morning and got the incompatible - removed message.  Immediately after I got a message about a new version of lightning being available. I installed it and my couple events are there.  Sort of an awkward way to go about it -- uninstalling then offering a new version but that's how mine went.

---

