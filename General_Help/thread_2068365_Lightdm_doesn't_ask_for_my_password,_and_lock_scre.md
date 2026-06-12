---
title: "Lightdm doesn't ask for my password, and lock screen doesn't work"
date: 2012-10-09
forum: General Help
---

### Post by supercheetah on 2012-10-09
I temporarily disabled my password for my account, and then re-enabled it (or at least tried to).  I did this properly from System Settings->User Accounts, but when I tried to set the password back again, it froze on me, and didn't take my new password, so I tried using *passwd* to change it, but that didn't solve the problem.

Now when I lock the screen, the password prompt just gets frozen, and I have to restart Lightdm from a virtual terminal, and Lightdm doesn't ask me for a password, but rather just has me click the Login button.

I really don't want to leave this unsecured like that.

Does anyone have any idea what's going on here?

---

### Post by supercheetah on 2012-10-10
For anyone that runs across this problem in the future, I figured out the answer from [this link]("http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm").

Essentially, what happened was that the user was not removed from the *nopasswdlogin* group.  Running the following command solved the problem:

```

sudo gpasswd -d username nopasswdlogin

```

---

