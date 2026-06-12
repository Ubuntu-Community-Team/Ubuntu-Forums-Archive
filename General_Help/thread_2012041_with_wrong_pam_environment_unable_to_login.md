---
title: "with wrong pam_environment unable to login"
date: 2012-06-28
forum: General Help
---

### Post by tigerswing2 on 2012-06-28
Hi,

I made some mistakes in ~/.pam_environment file, the wrong changes caused the login failure. I could not login in system. I only have one super account. And I tried to press ctrl-alt-f1 to enter into full screen login mode, however I still couldn't login.

Can any body help?

Many thanks.

tiger

---

### Post by moore.bryan on 2012-06-28
Try going into a LiveCD/USB session, mounting your /home, and fixing the permissions there.

Just ask if you need more than that...

---

### Post by tigerswing2 on 2012-06-28
Thanks for the reply moore.

Can you explain a little more about permission fixing? What are the detail I need to do?

---

### Post by moore.bryan on 2012-06-29
What I was suggesting was to launch a live session, mount your /home in a terminal or via Nautilus, and re-edit the ~/.pam_environment file to remove any mistakes.

Or, did I misunderstand your initial problem and you made some changes, but don't know what the mistakes are? That's a different horse.

---

