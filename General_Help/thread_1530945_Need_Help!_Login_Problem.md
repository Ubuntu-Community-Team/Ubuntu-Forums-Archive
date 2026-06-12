---
title: "Need Help! Login Problem"
date: 2010-07-14
forum: General Help
---

### Post by DedMoroz on 2010-07-14
Long time Ubuntu user and have come across a new challenge. Any help on this would be greatly appreciated as the computer is my main system at home.

OK, here are the steps I took...

System > Admin > Users & Groups

Up comes a pop up screen that shows my account info. On one line it says:

Password : Asked On Login (change...)

So... :) I clicked "change" and entered my password. Then I clicked "dont ask my password at login".

After rebooting, I can no longer get into my desktop. The system boots up fine, makes it to the login screen and when I click my name (not needing a password anymore) the OS tries to boot up and then nautilus and everything basically fails because I had originally created an encrypted /home directory when I installed the OS.

I need help on this one. Not sure how to approach it. I get a few error messages when it tries to log in, but i dont recall what they are since Im at work now. Any help would be greatly appreciated, thanks!!!

---

### Post by jward3010 on 2010-07-14
This is a little strange as you haven't changed or removed your password, just prevented the need to provide it at boot time. I'll think on it.

---

### Post by DedMoroz on 2010-07-14
Thanks for any advice. I'll post my error messages when I get home tonite. Maybe those will help out.

---

### Post by DedMoroz on 2010-07-14
so the problem im having is a setting i hanged in "users-admin". im not sure what i would do if i was doing that from the command line though.

---

### Post by DedMoroz on 2010-07-14
OK. I solved my problem.

After logging in, I got these error messages...

> could not update ICEauthority file /home/myname/.ICEauthority

and another error popped up...

> there is a problem with the configuration server, (/usb/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

after i closed those out, I got lucky. Faced with a blank screen (but able to see my wallpaper) i gave ALT+F2 a try and it worked. I was then able to type in "users-admin" and readjust my settings back to what i had!

---

### Post by jward3010 on 2010-07-15
Good stuff, did that cause the desktop to come back properly?

Although it's still crazy that a single option unrelated to anything major caused something so catastrophic.

---

