---
title: "Switch User goes to Lock Screen"
date: 2010-05-28
forum: General Help
---

### Post by dleonov on 2010-05-28
I have a problem with Switch User on a newly installed Ubuntu 10.04 on Asus Eee 1101ha. 

When I try to use Switch User, I just get to the Lock Screen of the currently logged in user, where I'm asked to enter a password.

There is also "Switch User" button on the Lock Screen - the screen gets black and then gets back to the same Lock Screen. Login Screen is not displayed.

If I logout I can login with a different user, but Switch User doesn't work.

Any ideas?

---

### Post by jerrrys on 2010-05-29
navigate to here and change

[ATTACH]158649[/ATTACH]

---

### Post by dleonov on 2010-05-30
I tried selecting "Don't ask for password on login", but it doesn't help. I can login without password, but whenever I select "Switch User", I get "Lock Screen" - the same screen I get when pressing CTRL+ALT+L.

I also DO WANT to have passwords on the accounts and when I select "Switch User", I want to get "Login Screen" where I can login with a different user by entering password, but I don't get "Login Screen" - I get "Lock Screen" instead.  On this "Lock Screen" I'm asked for current password and if I enter current password, I get back to current  account. I can't login with different user without logging out first.  So, "Switch User" is definitely broken...

I tried invoking "gdmflexiserver -xnest" and "gdmflexiserver" - and I get the same result, I get "Lock Screen" where I'm asked to enter the password of current user...

Does anybody have same issues? Any recommendations what should be checked?

---

### Post by mbsullivan on 2010-07-08
BUMP.

> I tried selecting "Don't ask for password on login", but it doesn't help. 

I also am having THIS issue... Switching users ALWAYS seems to pull up the Lock Screen, regardless of whether not the current account has a password.

Unfortunately, the lock screen does not accept a blank password for accounts that do not have passwords. FAIL. :(

Switching users without switching back works, though, as of 6/8/10 (at least for me).

Mike

PS: I just threw up in my mouth a little bit.

---

### Post by flocko on 2010-09-29
I have the exact same problem - also on an Asus Eee 1101 with Ubuntu 10.04.
Looking forward to find solutions..
Thanks,
Flocko

---

### Post by dleonov on 2010-09-29
I still didn't find any solution. It has something to do with the hardware. I have Ubuntu 10.04 on 2 laptops. On Dell switch user works without problems and on Asus Eee 1101HA it doesn't work... Maybe because of the video card?

---

### Post by kreichl on 2010-10-26
Switch User behavior is configurable via

  bash> gconf-editor
  ...
  desktop->gnome->lockdown->disable_lock_screen

After activating this switching away from a user does not activate lock screen.
Never!!!  So better you trust your guys ;-)

cuK

---

### Post by SentientFluid on 2010-11-02
> **kreichl said:**
> Switch User behavior is configurable via

  bash> gconf-editor
  ...
  desktop->gnome->lockdown->disable_lock_screen

After activating this switching away from a user does not activate lock screen.
Never!!!  So better you trust your guys ;-)

cuK

I believe this also needs to be done in each user account that you don't want to enter a password for.

---

### Post by dleonov on 2010-11-04
Disabling lock screen doesn't help - switch user still doesn't work.
When I try to switch user, screen blinks several times and then I get back to my desktop (it is not switched to a different user)...

---

### Post by MihaiCapot&#259; on 2011-12-27
It's a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/55575](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/55575)

---

