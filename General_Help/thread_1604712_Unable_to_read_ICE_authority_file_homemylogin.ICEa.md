---
title: "Unable to read ICE authority file /home/mylogin/.ICEauthority"
date: 2010-10-24
forum: General Help
---

### Post by trasgo77 on 2010-10-24
Hi! after update i cant log into my login account. I cant go into home/mylogin directory. 

Unable to read ICE authority file /home/mylogin/.ICEauthority

---

### Post by ajgreeny on 2010-10-24
Perhaps for some reason the ownership of the file has changed.

In a terminal run the command ```
ls -la .ICEauthority
``` which should give you an output of something like this.
```
-rw------- 1 username username 104990 2010-10-24 17:16 .ICEauthority
```If the *username username* entries are not the same as your login username, or the permissions at the start of the line (-rw-------) are not the same as here, something has gone wrong.

If this is the case, reboot to recovery mode from the grub menu and then run the command ```
chown -R username:username /home/username
```Now try running again as user by rebooting to your normal username.

Come back again if that does not help.

PS:  Where I have written "*username*" in this post, you should type your normal username, (or that is what the output should be) it should not actually be "username"

---

### Post by Colin@oxford on 2010-10-27
I have just had the same experience - the .ICEauthority file says it is owned by "root".  I have changed it back to me.

---

