---
title: "Guest Session Questions"
date: 2010-06-16
forum: General Help
---

### Post by sunshinecorp on 2010-06-16
I was wondering... when you start a guest session, does it create a /home/guest directory to save program settings and/or files, or do they go to /tmp or something similar and get deleted on log out? Also, which settings do programs follow. Default ones or ones originating from the account from which the guest session was started? How can one force specific settings and/or programs on a guest session (and disable the guest user from changing them)?

---

### Post by bodhi.zazen on 2010-06-17
google search kiosk + gnome or kiosk + kde for some nice reviews on this.

To some extent you can configure this behaviour and you can confine the guest account further with apparmor.

If you want to have standard settings for the guest account, edit the settings in /home/guest.

If you want the guest account to have a different home directory, use usermod or mount bind a new home.

---

