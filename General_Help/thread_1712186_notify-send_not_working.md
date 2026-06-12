---
title: "notify-send not working"
date: 2011-03-22
forum: General Help
---

### Post by MooPi on 2011-03-22
I'm trying to get notify send to display time as I've done in the past on 10.04. Here is my script: ```
DISPLAY=:0.0; notify-send -i clock "$(date +"%H:%M")"
```
Can't get it to work in 10.10

---

### Post by tgalati4 on 2011-03-22
Your script works under Jaunty.

What does the following say:

apt-cache policy notify-osd

tgalati4@tpad-Gloria7 ~ $ apt-cache policy notify-osd
notify-osd:
  Installed: 0.9.11-0ubuntu3
  Candidate: 0.9.11-0ubuntu3
  Package pin: 0.9.11-0ubuntu3
  Version table:
 *** 0.9.11-0ubuntu3 1001
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
        100 /var/lib/dpkg/status

----------------

Does it work without the DISPLAY variable?

notify-send -i clock "$(date +"%H:%M")"

---

### Post by stinkeye on 2011-03-22
Works here on 10.10.
Is **libnotify1** installed?

---

### Post by MooPi on 2011-03-22
Okay the problem is libnotify is installed but libnotify-bin isn't.
All solved and ready to notify.Thanks.

---

### Post by stinkeye on 2011-03-22
All good.
Here's a tip I just picked up...
If you use **-u critical** the notification will show when running fullscreen apps.

ie
```
notify-send -u critical -i clock "$(date +"%H:%M")"
```

---

