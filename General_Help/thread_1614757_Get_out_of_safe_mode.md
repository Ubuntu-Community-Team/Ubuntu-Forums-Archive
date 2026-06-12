---
title: "Get out of safe mode?"
date: 2010-11-06
forum: General Help
---

### Post by Chipmunkor on 2010-11-06
OK, I accidently got stuck in safe mode from login screen settings, and now i cannot get back, it wont let me unlock???

---

### Post by yetiman64 on 2010-11-06
> **Chipmunkor said:**
> OK, I accidently got stuck in safe mode from login screen settings, and now i cannot get back, it wont let me unlock???

I need you to clarify this a bit here as to what you mean by "safe mode".

Did you use a entry from the Grub boot menu ie a "recovery console" ?

Or did you login to a failsafe Gnome session from the login screen ? (Not likely to be a problem as such)

Or did you use the "lock screen" function from the power button in the "Indicator Applet Session" applet and can't authenticate from there ?

Or did you use a tty terminal (CTRL + ALT + F# where # can be 1 to 6 with 7 used to bring you back to the desktop)? Note that you need your username and password to login to tty terminals and if not logged in fully you can just use CTRL + ALT + F7 to return.

"Safe mode" is Windows terminology and leaves open quite a few possibilities for your problem. If you could elaborate a bit more as to how you ended up at the position you are in, I think it may be a bit more helpful for you.

---

### Post by sikander3786 on 2010-11-06
I think he is talking about failsafe Gnome and he made it his default session.

To the OP: Look under System > Administration > Login Screen and choose the default session you want to login to.

Alternatively you can logout and from the login screen, click your username and sessions menu will appear in the bottom of screen. Choose the session you want to login to, type your password and choose to set as default session when prompted.

---

### Post by yetiman64 on 2010-11-06
> **sikander3786 said:**
> I think he is talking about failsafe Gnome and he made it his default session.....
@ sikander3786, Yes, that would make more sense to me now, didn't think about setting the session as default, thanks. Will be interesting to see if it is the case.

---

### Post by Chipmunkor on 2010-11-06
Yes, I think that is the case but my main problem is, I have set it to autologin, and when I go to change the default session, I press unlock and nothing happens?????

---

### Post by sikander3786 on 2010-11-07
> I press unlock and nothing happens?????

Pressing unlock should bring up a password box and if you type your correct password, it should unlock. Doesn't it?

No matter if it is set to auto login, simply logout and you'll be on the GDM login screen. You can try it that way.

---

