---
title: "After updating to 11.10 it won't let me back into my user"
date: 2011-10-15
forum: General Help
---

### Post by freshtealeaf on 2011-10-15
Hi there

I have a user account (lets call it user1) that was the first account (sudo account) I made and my primary account that I use on this laptop (Thinkpad T510).

I created another account called darwin, just as a regular user in case a guest wants to use my computer. It has a password.

Ever since I updated to Ubuntu 11.10 (earlier today) from 11.04 it won't let me into my user1 account. It simply goes blank, brings up the console and then brings me back to the user login menu. 

So - long story short I'm logged in to my darwin account (thank god I have it, otherwise I'd have to find my ubuntu boot USB) and posting on the forums for help

Can anyone help me understand why my original sudo account (user1) isn't working after this upgrade? :confused:

---

### Post by freshtealeaf on 2011-10-15
This is just great. I realized there's no classic GNOME interface in 11.10, that's what I used in 11.04.

---

### Post by zdea on 2011-10-22
I think you must be experiencing the same issue as me however I do not have another user account to log in with. When the console pops up it is only to show an error having to do with "Plymouth". I think this has widely been reported but I haven't found a solution yet.

---

### Post by zdea on 2011-10-22
Actually for me it turns out that "Plymouth" thing was a red herring and I found somewhere else a hint that if it could be a locked .Xauthority file (located in your home folder) which I removed with the rm command on another virtual terminal and sure enough I was able to login. Go figure. So in short, if you are stuck at the login screen after upgrading, hit control-alt-f1 to bring up a virtual terminal, login, and type:
rm .Xauthority

If it asks you to remove the write protected file then you may be in my boat, say yes, and then hit control-alt-f7 to get back to the login screen and login.

---

