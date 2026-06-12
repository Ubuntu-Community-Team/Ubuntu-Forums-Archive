---
title: "Password none--can't authenticate"
date: 2012-03-14
forum: General Help
---

### Post by Ralph L on 2012-03-14
Just installed Oneiric and gnome-session-fallback.  During ubuntu install I set my admin user and password.  Later under System Setting>User Accounts I set my password to "none".  Now when I use sudo, it won't accept my password to authenticate.  Went pack to User Accounts and tried to change my password--can't unlock User Accounts, because it won't accept my password for authentication.  Clicked on password and window came up to change password, but won't allow change.

Anybody know what to do short of reinstalling oneiric??

Thanks in advance

Ralph

---

### Post by MG&amp;TL on 2012-03-14
Hold shift immediately after bootup to get to a black/purple screen (grub). Select "Ubuntu blah-deblah, kernel blah, (Recovery Mode)". Select "root prompt", then type:

```
passwd <username>
```replacing <username> with your username, (exactly, and case-sensitive), then enter a password twice. (you can't see it).

After that, reboot, and use your new password.

---

### Post by yetiman64 on 2012-03-14
> **MG&TL said:**
> Hold shift immediately after bootup to get to a black/purple screen (grub). Select "Ubuntu blah-deblah, kernel blah, (Recovery Mode)". Select "root prompt", then type:

```
passwd <username>
```replacing <username> with your username, (exactly, and case-sensitive), then enter a password twice. (you can't see it).

After that, reboot, and use your new password.

This is it, just note if it fails, try again and try the option to "remount all drives read/write". If the root drive is not being mounted (writable) redoing the password can fail.

If you need to remount the drives read/write choose that option, then just repeat the "drop to root shell prompt' option and the command MG&TL gave.

Had a password reset fail on me only yesterday and when using the command "ls /home" to see the users on the system got a blank response. Remounted all drives read/write, ran the "ls /home" command again and they were there -- the password change then was accepted. Good Luck.

---

### Post by Ralph L on 2012-03-14
Thanks.  It worked.  Had to do the remount drives read and write thing.

Ralph

---

### Post by yetiman64 on 2012-03-14
> **Ralph L said:**
> Thanks.  It worked.  Had to do the remount drives read and write thing.

Ralph
Good to hear :-), Please mark the thread as solved from the thread tools drop down menu in your browser window. Link #5 in my sig has instructions if needed.

Regards, yetiman64

---

