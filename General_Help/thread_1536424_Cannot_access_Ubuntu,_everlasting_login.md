---
title: "Cannot access Ubuntu, everlasting login"
date: 2010-07-22
forum: General Help
---

### Post by Pharanoise on 2010-07-22
Hi everyone, i've recently updated Ubuntu fully, installing even the 'proposed' updates,
the fact is, that after i've done so, i cannot login anymore.
All i can do, is select the user and insert the password, once done, the screen goes black for less than a second, (showing some kind of shell message, which can't be read, because there's not enough time), and then prompts me for login again.
All i can do is login again and again, i always get the login screen again.
What can i do?

---

### Post by Pharanoise on 2010-07-22
Can anyone help me?
All I figured out this far is that it's a GNOME issue, it crashes when i authenticate, and when it does, it prompts me for login again.

I've tried this:
```
sudo aptitude reinstall ubuntu-desktop
```

And i've also tried following some instructions into a blog, which said that the solution was erasing some gnome hideen directories in my home folder, (.gnome2, and many others), but i had no results.

I still keep getting the login screen on and on.
Any tip to follow?

---

### Post by varunendra on 2010-07-23
Can you please provide links to the blogs you followed? As far as I remember, removing .Gnome or related folders was a solution to 'Keyrings' related problems.

Try changing your password from root shell. To do so, press and hold 'shift' while booting, this will bring up grub menu. Select recovery mode and then 'root'. This will drop you to a root shell. Then enter this command:
```
passwd userId
```
(replace "userId" with your own user ID, you can verify it by** ls /home** command)
You'll be asked to enter a 'New Unix password'. Type a new one, press enter (you won't see any text while typing a password). Retype and press enter again. Then reboot ```
reboot
``` and try logging in with your new password.

---

