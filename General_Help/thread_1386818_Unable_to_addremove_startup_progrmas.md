---
title: "Unable to add/remove startup progrmas"
date: 2010-01-21
forum: General Help
---

### Post by allsaythat on 2010-01-21
Hi,
I'm unable to change startup programs. If I try and add or remove a program, any changes I have made seem to undo themselves. I suspect it might have something to do with being unable to save the session, but I really don't have a clue. Any ideas?

Just in case it makes a difference: I'm actually running Mint (Helena).

---

### Post by Brandon Williams on 2010-01-21
After you make a change, open a terminal and run: ls -l ~/.config/autostart/

There should be a .desktop file in that directory associated with the application you tried to add or remove. Has that file been updated as a result of the change you made? 

If the file has been updated and its content appears to represent the change you made, then maybe there's something in ~/.xsession-errors to indicate what the problem might be.

---

