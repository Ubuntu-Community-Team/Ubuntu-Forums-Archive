---
title: "What's slowing down my login?"
date: 2012-06-17
forum: General Help
---

### Post by x-shaney-x on 2012-06-17
During alpha and beta testing of 12.04, I noticed the time from login screen to loaded desktop was taking an age, around 20-30 seconds.
I found a command that shows hidden entries in startup commands and after disabling many un-needed items (gwibber, chat, blutooth etc) I found the desktop would load in less than 5 seconds.

Well since release, I have the slow login issue again.
I disabled the hidden services and I have actually disabled more stuff this time but the login is still averaging 20 seconds.

I just cannot work out what's holding it up.
I did a fresh install just a few hours ago and made sure I haven't installed anything that adds startup entries yet (dropbox and gm-notify) so they aren't to blame.

---

### Post by HunterDX77M on 2012-06-17
How do you delete these hidden services?

---

### Post by x-shaney-x on 2012-06-17
I didn't delete them, just disabled them.

The command is: ```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
``` and the entries will then show up in startup items.

Though people should only disable anything they are sure they don't need, not just disable stuff willy-nilly.

---

### Post by x-shaney-x on 2012-06-18
Should point out, this only happens when booting up the computer or rebooting.
If I log out then back in again, the desktop loads instantly.

---

