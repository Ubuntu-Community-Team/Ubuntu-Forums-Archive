---
title: "&quot;switch user&quot; button does not appear on lock screen anymore"
date: 2009-11-07
forum: General Help
---

### Post by crazycatlady0 on 2009-11-07
After upgrading from 9.04 to 9.10, the "Switch User" button disappeared from the lock screen.  I am running gdm and kde.

In v9.04, I could lock my screen and then another user could click the "Switch User" button.  This button allowed them to choose a session to login to, or to start a new session.

After upgrading to 9.10, this functionality has disappeared -- the button simply is not there.  There is, however, a "switch user" button on the main menu.  Howeer, when I click this button, it simply locks my screen.   At this point, the user cannot login unless they know the current users password to unlock the screen.

thanks in advance :)

---

### Post by m0urs on 2009-11-09
Same here. I installed the 9.10 Netbook Remix edition on my eeePC and when the screen is locked only the current user can unlock it. No chance to switch to another user.

This is very bad as no other users can do anything including shutting down the machine.

Any idea? Thanks a lot.

---

### Post by startswithaj on 2009-11-10
I'm also having this issue. This is very frustrating because I want to be able to keep a couple programs running in the background and allow my roommate to use it at the same time.

I might just have to go back to 9.04.

---

### Post by crazycatlady0 on 2009-11-10
is there an easy way to go back to 9.04?

this bug makes this OS unsuitable for my family's needs... 

does anyone know how we can properly submit the bug to the developers?

---

### Post by m0urs on 2009-11-11
I have solved the issue for me!

I installed the program "gconf-editor" and changed the following GNOME setting

/apps/gnome-screensaver/user_switch_enabled

to "TRUE".

After that it worked without a problem :-)

---

### Post by crazycatlady0 on 2009-11-11
> **m0urs said:**
> I have solved the issue for me!

I installed the program "gconf-editor" and changed the following GNOME setting

/apps/gnome-screensaver/user_switch_enabled

to "TRUE".

After that it worked without a problem :-)


Mine was already set to TRUE.  This did not solve my problem.

---

### Post by rfdias on 2009-11-22
> **crazycatlady0 said:**
> Mine was already set to TRUE.  This did not solve my problem.


Same thing here. Changed the setting in all user accounts and still don't work. There are 6 people in my house and just 2 computers, we need the "switch user" a lot.

---

### Post by crazycatlady0 on 2009-11-22
I have switched to kdm and the switch user feature works now.  There are a few other issues I had to resolve after switching to kdm.

---

### Post by rfdias on 2009-11-22
Solution found!

Must correctly set

/desktop/gnome/lockdown/disable_user_switching

AND

/apps/gnome-screensaver/user_switch_enabled

"Switch user" button is back! :D

---

### Post by Pithikos on 2010-06-29
Well in my case the problem is not that I don't have the button. I have the button there but when I click it the screen goes black. When I move the mouse then I get the same window thingy to unlock or switch user. If I finally unlock the screen then in the desktop I see some error messages "Unable to start new display. The name org.gnome.DisplayManager was not provided by any .service files" Oo

---

