---
title: "How to make ibus start up automatically and quitely!"
date: 2011-01-20
forum: General Help
---

### Post by northfly on 2011-01-20
Hello, I used to input Chinese with scim input method, which can be trigered by Ctrl^Space. But this time, I reinstalled ubuntu 10.04, I have to manually start up ibus from System>Preference>ibus firstly before I can triger the input method by Ctrl^Space.

This is not over, the key problem is there are several dialogues to click "ok" with before I can really use the scim.

How can I make this ibus startup automatically and quitely?

I tried put command "ibus -setup" into my .profile, it does start up the ibus automatically every time when I login, but the dialogues still bothering me.

Please help me out, thanks!

---

### Post by sanguinoso on 2011-04-08
Add ```
/usr/bin/ibus-daemon -d
``` to your startup scripts. If you don't know how follow these steps:

1)Go to System > Preferences > Startup Applications.
2)Click the Add button
3) For name type iBUS Daemon and for command type the following:
```
/usr/bin/ibus-daemon -d. 
```
4)Click Add to confirm.

Oh and sorry for the slow response.

---

