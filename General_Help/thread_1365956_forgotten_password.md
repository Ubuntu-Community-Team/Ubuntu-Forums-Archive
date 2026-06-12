---
title: "forgotten password"
date: 2009-12-27
forum: General Help
---

### Post by dkmiles on 2009-12-27
Somehow, I've forgotten my administrator password so that I can add programs to my hard drive. Short of reinstalling everything, is there any simple way to undo this so I can reenter a new password?

---

### Post by taurus on 2009-12-27
You mean you've forgotten your own password?  If you are the first user (the one that you created during the installing process), then you can use your own password when you run a command with the root privilege.

---

### Post by dkmiles on 2009-12-27
Yes, I can't believe I did it, but the password I created when I first started the computer and set myself as the administrator - I've forgotten. I realize this is real dumb, but I did it. Can I undo this mistake so that I can enter  another password. I do have my username, but that doesn't help if you don't have your password.

---

### Post by taurus on 2009-12-27
At the GRUB menu, pick the recovery mode and boot from it.  Then at the prompt, change your password.

```
passwd <username>
```
Replace <username> with your login name.  Once you have created a new password, reboot.

```
shutdown -r now
```

---

### Post by sisco311 on 2009-12-27
> **dkmiles said:**
> Yes, I can't believe I did it, but the password I created when I first started the computer and set myself as the administrator - I've forgotten. I realize this is real dumb, but I did it. Can I undo this mistake so that I can enter  another password. I do have my username, but that doesn't help if you don't have your password.

[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by dpdx on 2009-12-27
I think the same thing happened to me (I typed in an invalid password too many times). For me, I cannot get a command prompt screen because my applications aren't loading, including the system menus, which would give me access to command prompt. So I have no menu functionality and no icons load on the desktop.:(

Thanks for any clues!

---

### Post by dpdx on 2009-12-27
I've been able to edit user passwords and the root password. But how do you update the password you're prompted on upon powerup?:confused:

Tried F2 as well as ESC during boot. Nothing seems to affect the password at bottom of screen. I can't provide screen shot b/c I have no network connection with computer in question...

---

