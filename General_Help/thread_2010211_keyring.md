---
title: "keyring"
date: 2012-06-25
forum: General Help
---

### Post by MMcQuown on 2012-06-25
When I tried to access my backup files, I was referred to Ubuntu One and asked for a keyring password. When I installed 12.04, I don't remember seeing anything about an effing bloody keyring password. My regular password doesn't work. I've had a valuable document get reformatted so it's useless and I need the backup copy. I'm 72, I have emphysema and the heat is making me ill.  Can someone tell me how to get to the bloody keyring without having to re-install and losing all my backup files? So far, I have found trying to deal with Ubuntu One to be more trouble than useful.

---

### Post by maverickaddicted on 2012-06-27
Check if this helps you or not -

[http://ubuntuforums.org/showthread.php?t=1439669](http://ubuntuforums.org/showthread.php?t=1439669)

---

### Post by MMcQuown on 2012-06-27
Not quite. I can change a password, but not the keyring password, which it is asking for to authenticate my changing the password.....

---

### Post by maverickaddicted on 2012-06-28
Try removing the keyring directory -

```
rm -rf ~/.gnome2/keyrings
```

Logout and login back.

---

