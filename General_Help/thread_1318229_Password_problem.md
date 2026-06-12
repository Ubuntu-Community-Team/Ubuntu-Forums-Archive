---
title: "Password problem"
date: 2009-11-07
forum: General Help
---

### Post by tonto1950 on 2009-11-07
Installed 9.04 some weeks ago dual booting with Win XP and everything OK till today. 
It is now not accepting my password on login. When I begin to type it the actual letters are visible
When I enter the password it will not accept it and wants me to try again

I have not upgraded anything so why has this suddenly happened

Thanks in advance

---

### Post by hal10000 on 2009-11-07
Did you change your keyboard-layout or language settings?

You can change your password by booting to the recovery console and then perform
```
sudo chpasswd YOUR_NAME
```
instead of YOUR_NAME you have to use the username for whom you want to change the password.

When you type your new password, it will NOT be seen on the screen, and you will be asked twice to verify typing

---

### Post by tonto1950 on 2009-11-08
Have tried this but I keep getting "missing new password" in response
I tried several variations of the command but always get the same response

I have changed nothing on keyboard etc so this is a mystery.The other thing is why does it let me see the password when I type it into login screen ?
  My passwords on Windows work OK

---

### Post by hal10000 on 2009-11-08
The fact, that you can see your "password" lets me think that you are not being asked to type your password, but your username.
If you use gdm as your login manager, then you have to perform two steps to login:

1.) You are being asked to type your username (which will be displayed). You have to type the <ENTER> key after typing the username.

2.) After you hit the <ENTER> key you will be asked for your password, which will **not** be displayed as visible text.

---

### Post by tonto1950 on 2009-11-11
Thanks for your help. It was me being thick !  Not having gone into it for some time and being used to Windows login I was putting password into wrong screen.
Thanks again

---

