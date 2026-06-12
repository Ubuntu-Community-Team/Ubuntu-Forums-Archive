---
title: "Logout delay"
date: 2010-05-23
forum: General Help
---

### Post by st0nes on 2010-05-23
Hi all,

When I click logout or shut down I get a countdown saying I will be logged out or shut down in 60 seconds, then it counts down.  I can click the "shut down now" button, but I find this behavior incredibly irritating.  When I click logout I would like to logout NOW. Is there some way of turning off this annoying "feature"?

---

### Post by jamesisin on 2010-05-23
This is something that is theme dependent.  Some themes don't offer that dialog and delay.  I'm sure it's switchable but not sure how or where.

---

### Post by jubilee33 on 2010-05-23
> **st0nes said:**
> Hi all,

When I click logout or shut down I get a countdown saying I will be logged out or shut down in 60 seconds, then it counts down.  I can click the "shut down now" button, but I find this behavior incredibly irritating.  When I click logout I would like to logout NOW. Is there some way of turning off this annoying "feature"?

You can check out the instructions [here]("http://subbass.blogspot.com/2009/11/howto-disable-60-second-delay-in.html") to disable that 60-second delay feature.

---

### Post by st0nes on 2010-05-24
> **jubilee33 said:**
> You can check out the instructions [here]("http://subbass.blogspot.com/2009/11/howto-disable-60-second-delay-in.html") to disable that 60-second delay feature.
Thanks for the reply, but that doesn't work:
```
mark@addy-laptop:~$ gconftool-2 -s /apps/indicator-session /suppress_logout_restart_shutdown --type bool true
Error: Parse error: Didn't understand `/suppress_logout_restart_shutdown' (expected true or false)
```
How do I use gconf-editor?  I don't have it any menus.

---

### Post by Flyers2391 on 2010-05-24
> **st0nes said:**
> Thanks for the reply, but that doesn't work:
```
mark@addy-laptop:~$ gconftool-2 -s /apps/indicator-session /suppress_logout_restart_shutdown --type bool true
Error: Parse error: Didn't understand `/suppress_logout_restart_shutdown' (expected true or false)
```
How do I use gconf-editor?  I don't have it any menus.

Right click applications and select "edit menus".  Click on System tools in the new box and check the box next to "Configuration Editor"

---

### Post by st0nes on 2010-05-25
Thank you--that solves the probem.

---

### Post by jamesisin on 2010-05-25
Excellent.  Please mark your thread as SOLVED in Thread Tools above.

---

