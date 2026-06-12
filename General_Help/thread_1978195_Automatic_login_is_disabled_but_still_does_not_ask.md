---
title: "Automatic login is disabled but still does not ask for a password on login"
date: 2012-05-11
forum: General Help
---

### Post by Prescilla on 2012-05-11
Hello Ubuntu users.
Ubuntu 12.04

I have enabled the automatic login and set the password to None this morning so that my sister can use the computer using my account (administrator).

When I came back, I turned off the automatic login and change my password as well.

I also created a new user account for my sister to use and set it without a password but not to automatic login so that the login screen will still be displayed prompting the user which account to use on that session.

When I rebooted my computer, the login screen was displayed which is okay since I turned off the automatic login. I tried to click on the newly created user account and I was able to login without password and that should also be right. I log out of that user account and the login screen again appeared with the user accounts to choose from. 

Here's the problem. When I clicked on my user account, it didn't prompt for a password. I am sure and made sure that I change my password and the automatic login was turned off but still it does (do) not prompt for a password.

I've rebooted 5 times already and the same thing happens.
Any ideas? I really need for Ubuntu to prompt for a password on my user account (administrator).

---

### Post by kuifje09 on 2012-05-11
Are you shure you did not make a mistake?  I tested what you did.
Automatic login,  works fine
Ask for password again,  works fine, but I had to set a passwd. ( maybe I forgot one )

Now I have a question, why it is not done just with the passwd- and shadow- file.
Quite silly. 
When you kick the x from the passwd field in the passwdfile it just does its job as for ages.

If I was you I checked the passwd file contains the x in the passwd field, indicating to use the shadow file.
The shadow file contains the real (MD5 ? ) passwd

---

### Post by Prescilla on 2012-05-12
The automatic login is not the problem.
I turned it off and Ubuntu displays the login page prompting which user account to use. So it is working.

The problem is that when I click my user account, it does not ask/prompt for a password.
I am sure that I set up a password. In fact if I install anything via the software center or do a sudo it prompts for a password and my password works.

What I want is for Ubuntu to prompt a password on login. Which it should because automatic login is turned and I did setup a password. And yes the passwd file contains x.

---

### Post by Prescilla on 2012-05-13
Up

---

### Post by kuifje09 on 2012-05-15
Okay, I see, but sorry I cannot help you further. I do not use the pictograms to login as I do understand you are using ?
I have to type the name and paswd... Not the fancy MSwindows behavior.
I think you bump upon a bug  ...

Maybe switch the user interface on login will help at least for logging in once, then go back and see if the problem has gone ?

---

### Post by BertN45 on 2012-05-16
Same problem. I have tried different ways to get a password prompt again, but nothing worked.

---

### Post by kanikilu on 2012-05-16
Can you post the contents of /etc/lightdm/lightdm.conf ?

Have you guys tried what kuifje09 suggested about turning off the users list in lightdm?

Here is a how-to:

[http://www.tejasbarot.com/2012/04/25/howto-hide-users-list-from-login-screen-ubuntu-12-04-precise-pangolin-linux/](http://www.tejasbarot.com/2012/04/25/howto-hide-users-list-from-login-screen-ubuntu-12-04-precise-pangolin-linux/)

It suggests vi, but of course you can always use your editor of choice. After a reboot, it should ask for a username, see if it requires a password now. If so, you can keep it like that if you want. Or if you prefer the users list, try reversing the process and then try again. If it still doesn't work, maybe you've indeed stumbled upon a bug??

---

### Post by Prescilla on 2012-06-15
thank you for the response.
i wasn' t able to solve this problem but i reinstalled ubuntu and so it is now working.

---

### Post by mastabog on 2012-09-29
Damn, I hit the same problem and was hoping this thread to show a solution. Reinstalling Ubuntu is too extreme (it's not the Windows world).

Nobody can suggest a fix?

---

### Post by mastabog on 2012-09-29
Found a solution here: [http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm](http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm)

The user got placed in the nologinpasswd group. I had to remove it from there using: ```
sudo gpasswd -d myusername nopasswdlogin
```

This is a bug that Ubuntu should fix. I'm using 12.04.

---

### Post by Raygreen on 2012-12-30
[FONT="Comic Sans MS"][COLOR="Teal"][SIZE="3"]That worked for me. I was hoping not to have to reinstall Ubuntu after just getting everything set up the way I like it. I had turned off the password and then later decided I wanted to put it back on. It would not work through the Users Account window. But using that simple Terminal command got it working again.[/SIZE][/COLOR][/FONT]

---

### Post by ab4rl1 on 2013-04-15
> **mastabog said:**
> Found a solution here: [http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm](http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm)

The user got placed in the nologinpasswd group. I had to remove it from there using: ```
sudo gpasswd -d myusername nopasswdlogin
```

This is a bug that Ubuntu should fix. I'm using 12.04.

I had the same problem today. The command line fix worked for me. I filed a bug report if anyone wants to confirm it:

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1169054](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1169054)

---

### Post by Nuxer-India on 2013-05-13
> **mastabog said:**
> Found a solution here: [http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm](http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm)

The user got placed in the nologinpasswd group. I had to remove it from there using: ```
sudo gpasswd -d myusername nopasswdlogin
```

This is a bug that Ubuntu should fix. I'm using 12.04.

Thanks. This worked for me.

---

### Post by cybertrail on 2014-04-25
Wanted to bump this up and say I just had the same problem and this solution fixed it.  Thanks!  (and I'm using 14.04 so this bug has still not been fixed)

---

