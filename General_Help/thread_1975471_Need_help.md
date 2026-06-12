---
title: "Need help"
date: 2012-05-07
forum: General Help
---

### Post by botokiller on 2012-05-07
Hi again.
After I typed "sudo su" in terminal and restarted computer i got all pannels turned grey and most items in "system" menu. How do I get everything back?
P.S. sorry for noob questions.

---

### Post by Cheesemill on 2012-05-07
Just typing 'sudo su' in the terminal wouldn't cause this sort of problem by itself (although it isn't a good idea).

Did you type any else after this before restarting?

---

### Post by botokiller on 2012-05-07
I tried to install gimp. The theme changed to the one of root, thats why i think that the sudo su caused problem. It seems like gnome loads from root.

---

### Post by jadtech on 2012-05-07
have you tried logging off and back in as your self ??

---

### Post by Cheesemill on 2012-05-07
This is why you shouldn't ever use 'sudo su', it can change the permissions on crucial files in your home folder so that your user cannot access them anymore.
Instead you should use 'sudo -i' to get a root shell if you ever need one.

Anyway, try this to fix your permissions:
```
sudo chown -R user.user /home/user
```
replacing all instances of user with your actual username.

Log out and back in again and you should be sorted.

---

