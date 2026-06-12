---
title: "How To Really Disable Login After Waking From Suspend?"
date: 2012-06-03
forum: General Help
---

### Post by buzzingrobot on 2012-06-03
I'm running 12.04 with Gnome Shell 3.4.2.  How do I convince it to stop requiring a password when it wakes up from suspend?

I think I've found all the obvious places in settings to turn it off.  It's still there.

---

### Post by sant on 2012-06-03
Applications >  Brightness and Lock

---

### Post by buzzingrobot on 2012-06-03
> **sant said:**
> Applications >  Brightness and Lock

Done first thing after install. I'm still prompted for a password to unlock.

---

### Post by wilee-nilee on 2012-06-03
> **buzzingrobot said:**
> Done first thing after install. I'm still prompted for a password to unlock.

Does it look like this?

[ATTACH]219163[/ATTACH]

---

### Post by Deepak J on 2012-06-03
same with me

even I tried it loads of times but in vain.

---

### Post by buzzingrobot on 2012-06-04
> **wilee-nilee said:**
> Does it look like this?

[ATTACH]219163[/ATTACH]

Yep.

---

### Post by apsot on 2012-06-26
i'm facing the same problem. It's interesting that if i log in with unity instead of gnome the problem goes away

---

### Post by apsot on 2012-07-01
well, i think i found a "solution". I disabled lock screen in general. By doing so, your pc can't be locked, not even after waking up from suspend. As a result you don't have to give your password every time it wakes up.

here is what i did:
1. open dconf editor
2. go to org/gnome/desktop/lockdown/
3. check the disable-lock-screen box on the right as shown in the screenshot

---

