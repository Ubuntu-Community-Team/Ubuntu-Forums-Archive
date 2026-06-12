---
title: "Getting Thunderbird to open links with Chromium"
date: 2011-01-19
forum: General Help
---

### Post by WebDrake on 2011-01-19
Hello all,

I'm having trouble getting Thunderbird to open links using Chromium (chromium-browser).

The default browser is now set to chromium-browser in KDE system settings.  I've also tweaked the Thunderbird config network.protocol-handler.app.http and https settings to use chromium-browser or /usr/bin/chromium-browser.

Despite this, Thunderbird keeps opening links in Firefox.  I'm bewildered as to why.

One thought is possibly an old GNOME system setting (there are .gconf and .gnome2 directories in my home directory, though I no longer use GNOME or have it installed on my system).  But I don't know and I would have thought the Thunderbird config would have overridden that in any case.

Can anyone advise?

Thanks in advance,

    -- Joe

---

### Post by Brandon Williams on 2011-01-21
I had this problem and tried every config-fix I could find. Nothing worked. Then I installed the [BrowsrBounce](https://addons.mozilla.org/en-us/thunderbird/addon/browsrbounce/) extension, and it solved the issue nicely.

---

