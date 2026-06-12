---
title: "Suspend crash"
date: 2012-07-24
forum: General Help
---

### Post by bilboubu on 2012-07-24
xbmcbuntu upgraded to 12.04 LTS

The screen goes blank but the power led hd fans etc stay on and there is no way to resume other than kill the power.

I am not sure where to begin but after a quick look at the many threads one suggested the pm-suspend log as a start and I can only see one fail, could it be this???

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


whole log:
[http://pastebin.com/JbwqvQSA](http://pastebin.com/JbwqvQSA)

---

### Post by bilboubu on 2012-07-24
I think it is tvheadend as when not running it suspends. Damn hoow the heck do I get round this, darn it.

---

