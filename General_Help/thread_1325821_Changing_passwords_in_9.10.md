---
title: "Changing passwords in 9.10"
date: 2009-11-13
forum: General Help
---

### Post by fballem on 2009-11-13
I'm wondering if anyone else is having problems changing the password in 9.10? I select System > Peferences > About Me > Change Password.

I am able to authenticate myself. I type in the new password (twice) and select the Change Password button. At that point, the system seems to try and update, but it never completes.

If there is a solution, I would be most grateful.

Thanks,

---

### Post by mikewhatever on 2009-11-13
Not sure what's wrong there or how to fix it, but you could try the Lost Passwrd howto meanwhile.
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by fballem on 2009-11-13
> **mikewhatever said:**
> Not sure what's wrong there or how to fix it, but you could try the Lost Passwrd howto meanwhile.
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

Thanks for this - fortunately, I haven't lost my password - it just doesn't get changed. I can still log in using the old password.

---

### Post by mikewhatever on 2009-11-13
Regardless, the method should still work and change the password for you. It is also GUI independent, and thus not affected by bugs in, say, Gnome or KDE.

---

### Post by Qboy61 on 2009-11-17
I have the same problem.  I have tried changing the password in another spot System>Administration>Users and Groups.  It asks the same questions and after the new password is entered and "Change Password" is pressed I get an acknowledgement that the password was changed.  Yet upon logout and login...  Still old password!  This method was not a problem in 9.04.

---

### Post by WelterPelter on 2009-11-29
I am having the same problem. And help?

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
Same here and I can't delete a user within a GUI. I did both in the command line using "passwd user_name" and "userdel user_name". Hope they fix the GUI though.

---

### Post by john newbuntu on 2009-11-29
Yeah, I found the screen hanging too on Karmic 9.10 and kernel 2.6.31-15-generic.

As a workaround, just open up a terminal (Applications->Accessories->terminal) and type:
```
passwd
```
It will ask for the old password and then the new one twice. This works.

Similarly, to remove user, open a terminal and type:
```
sudo deluser jake
```
where jake is the user who needs to be removed.  This works too.

---

