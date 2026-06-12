---
title: "Login fails, ecryptfs-mount-private puts error"
date: 2012-02-20
forum: General Help
---

### Post by FetterChiller on 2012-02-20
Hello!
After the last update of my ubuntu (11.10) I can't login to my account anymore: As soon as I enter my password and press enter it will return to the login-screen.
I researched that and found that others had that problem before. The ESC-Fix (pressing the ESC key directly after the enter-key) doesn't work for me.
So I tried to delete some data from my encrypted partition or at least to save the data externally. So I logged in via Str-Alt-F1 and tried "sudo ecryptfs-mount-private" and got the error message:
ERROR: Encrypted private directory is not set up properly.

That's a little weird, I've been using my ubuntu for a few month now already...

I think the easiest for me would be to mount the encrypted partition, move all files (a lot of data I really need) to a external hard disk and reinstall ubuntu without encryption (I don't have too much knowledge about Linux, so I propably can't fix the problem).

Anybody any ideas what to do?

regards,
FC

---

### Post by FetterChiller on 2012-02-23
I could find myself a solution.
I loged into the guest account, pressed Cltr-Alt-F1 loged in there and used ecryptfs-**recover**-private . Like this I could access my data and copy it to an external drive.

Hope this helps s.o.
Greetzes!

P.S.: I can't find out how to mark this thread as resolved...

---

