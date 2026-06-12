---
title: "Blocked synaptics package handler"
date: 2009-07-10
forum: General Help
---

### Post by hokuskrokus on 2009-07-10
Can anyone help?

When I try to install anything, I get this message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I do as suggested, nothing happens. I idles forever. How do I get out of this?

---

### Post by drs305 on 2009-07-10
Welcome to the Ubuntu forums hokuskrokus!

Type it as it says:
```
sudo dpkg --configure -a
```

When you hit ENTER next it should then ask for your password - are you entering it? You won't see it as you type. That is a security feature. Type it and hit ENTER. Or have you done that and get the second line after entering your password?

If you entered your password correctly, try changing servers in Synaptic or Software Sources: Synaptic, Settings, Repositories, Download From window, and choose another or "Other".

If you still have problems, post this by ALT-F2 and entering the following in the command line:
```

cat /etc/apt/sources.list

```

---

### Post by hokuskrokus on 2009-07-11
Thanks for your welcome and for a fast reply.
Unfortunately I'm still experiencing troubles. I did what you wrote, and apparently it fixed Synaptics for a short while. But when I tried to urgrade some other programs, the system went down again. Synaptics unpacked some programs but at a point, it stopped. Then I get the same errormessage as I mention at first. Soon after, the pc freezes, and the only solution seems to pull the plug and battery to get it back to life.
Hope there's somethingelse to do.

---

### Post by QIII on 2009-07-11
Please post the last bit of the tty before the message.

It's hard to aim when you can't see what you are shooting at.

---

