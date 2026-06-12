---
title: "What is login keyring password?"
date: 2012-04-15
forum: General Help
---

### Post by Lucas Malor on 2012-04-15
[LIST=1]
[*]Empathy asked me the login keyring password. Is the root password?
[*]Why Empathy want that pass?
[*]Now when I boot ubuntu the password is asked every time, even if I choosed the autologin. I want the password is asked only when Empathy starts. How must I do?
[/LIST]

---

### Post by Rex Bouwense on 2012-04-15
I believe that it is the login password that you have opted not to use when you set up Ubuntu.
Some programs require a password to open.  I do not use empathy but apparently it requires a password.  It is stored on the on the keyring which is normally opened when you log in with your password.  Since you have opted not to use your password, it is merely asking you to open it.

---

### Post by raja.genupula on 2012-04-15
to get rid of , [http://www.thegeekstuff.com/2011/10/change-login-keyring-password/](http://www.thegeekstuff.com/2011/10/change-login-keyring-password/)

---

### Post by Lucas Malor on 2012-04-15
@Rex Bouwense: Ok, but what about questions number 2 and 3?

I found this thread: 
[https://bbs.archlinux.org/viewtopic.php?id=117781](https://bbs.archlinux.org/viewtopic.php?id=117781)
and I think it means Empathy requires the root password to decrypt IM account passwords stored with gnome-keyring. The bad thing is gnome-keyring - AFAIK - asks to unlock the passwords at every startup instead of asking it when it's required. And I can't ask Empathy to not store password with gnome-keyring for MSN...

Is there an alternative IM program that allow you to not store MSN password or doesn't use gnome-keyring? What about pidgin?

@raja.genupula: the problem is I have autologin and I don't want to remove it.

---

