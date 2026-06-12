---
title: "HELP- I created a second user, now Ubuntu won't boot!"
date: 2009-11-03
forum: General Help
---

### Post by sbelz79 on 2009-11-03
I'm running Ubuntu 9.08

I created a second user, a simple desktop user, simply by using the menu that comes up in the top right corner of the screen.  I switched to that user and logged in with the password.  When I logged out, the screen went white.  After a couple minutes of nothing happening, I hit the restart button on my box, and now Ubuntu won't boot correctly.  It goes to the Ubuntu screen with the progress bar, and when the progress bar completes, I get a bunch of messages, including one stating that GNOME failed to initiallize.  It then let me log in, and I have a command line, but that's it.  So, I figure, the problem started when I created a new user, so I deleted the new user account by temporarily switching to root user and typing:
userdel -r "username"

Then I shut down the computer and restarted it and I'm having the same problem.  Please help me recover my system!

---

### Post by sbelz79 on 2009-11-03
Sorry, I meant 9.04

---

### Post by sbelz79 on 2009-11-03
I also tried going into recovery mode and using all of the options available there to repair problems, including updating GRUB.  Still won't boot into anything besides the command line.

---

