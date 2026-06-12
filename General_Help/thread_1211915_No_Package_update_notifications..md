---
title: "No Package update notifications."
date: 2009-07-13
forum: General Help
---

### Post by Subban on 2009-07-13
I upgraded to 9.04 a week or so ago, and since then I haven't had any package update notification. I have had to manually open Synaptic and "mark all upgrades"

Has the update notification icon that used to pop into the system tray been done away with, or is something broken for me ?

---

### Post by pedro_orange on 2009-07-13
It works a little differently in 9.04

[http://www.ubuntu.com/getubuntu/releasenotes/](http://www.ubuntu.com/getubuntu/releasenotes/)

> Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by Subban on 2009-07-13
Thank you for the swift reply.

If I understand this correctly (after a quick google and read) it will only alert the user to normal none security related updates once a week (well, 7days) and this "timer" is based on when Synaptic or Add/Remove was used (and perhaps apt-get?) so is blindly reset without the user being aware?

Isn't this a real downgrade to the previous method of alerting via the icon in the system tray? I shall be reverting to the "old" (read that as more sensible) method of operation I think. I fail to see what was confusing that it had to be changed, I am really starting to wonder about the Gnome guys... I've tried Gnome Shell, 'nuff said.

"Randomly" opening windows on screen is something I expect more from Windows than Ubuntu.

</rant> Sorry.

---

