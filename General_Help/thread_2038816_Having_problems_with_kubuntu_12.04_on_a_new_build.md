---
title: "Having problems with kubuntu 12.04 on a new build"
date: 2012-08-07
forum: General Help
---

### Post by george-palmer on 2012-08-07
Hi,

I'm having a couple of problems with my new computer.
[LIST]
[*]At the login screen, somtimes the mouse and keyboard stop responding. Cursor is still blinking in login box.
[*]The system freezes, about twice a day, nothing responds and I can't SSH in. It's not related to load.
[*]I get black square artefacts on the screen, most commonly with chrome browser. The browser still functions but often not visibly, sometimes it slows down.
[*]Sometimes moun is unable to ask for a sudo password. I get the error "This operation cannot continue since proper authorization was not provided".  auth.log shows: 
```
07/08/2012 15:45:49	gopalmer-desktop-1	dbus[1167]	[system] Rejected send message, 2 matched rules; type="method_return", sender=":1.63" (uid=0 pid=4883 comm="/usr/bin/python /usr/share/apt-xapian-index/update") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.62" (uid=0 pid=4881 comm="/usr/bin/qaptworker ")

```
[/LIST]

The system spec is:
Intel Core i7-3930K
Asus P9X79-Pro motherboard
32GB RAM
1TB HDD
Nvidia 7600GT, twinview, 2x23" monitors

Any help would be really appreciated.

Thank you, George

---

