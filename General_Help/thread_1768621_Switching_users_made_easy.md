---
title: "Switching users made easy"
date: 2011-05-27
forum: General Help
---

### Post by jorritTyb on 2011-05-27
Hi, I'm trying to configure ubuntu 11.04 for my children so each of them has a different user. I already added the users and made sure no password is needed at login. However, the switch remains annoying. When one of my children is busy and then another one wants to do something he/she selects the right user in the top-right button. Things brings down the login dialog for that user again. That in itself is already annoying (why is that window shown when no password is required?) but then how does he/she go on from here? You can't simply login as then it will say the password is required. So he/she has to press 'Switch User' again and then select his/her username again. And only then is the switch complete. This is an awful lot of steps for simply switching users. Any way to make this faster?

A related problem is that when I want to shutdown the computer I have to go over all logged in users to manually do shutdown in all of them (or else use /sbin/shutdown -h now). This is also extremely annoying. My children only have a web browser open so I would like to just shutdown without having to switch to all users (which is hard due to the problem above).

Thanks,

---

### Post by LowSky on 2011-05-27
For why the password dialog comes up: Linux uses passwords. No Password is really just a blank password. It might frustrate you and your family, but the system has behaved that way for decades.

I tried to recreate the issue of having to attempt switching user, and it doesn't seem to happen for me. I hit switch user and it brings me to the login screen. I can then pick the user I want.

The other option is to make your user account a full administrator. Ubutnu by default names the first user a Custom user, as you have Sudo access. An admin wouldn't need sudo. which means full control of the system without extra passwords
Dangerous but possibly effective. Instead of shutting down look into using Hibernation. It saves the last used spot and might not need every user to be closed.

---

### Post by ExileAmongYou on 2011-05-27
> **jorritTyb said:**
> he/she selects the right user in the top-right button. Things brings down the login dialog for that user again. That in itself is already annoying (why is that window shown when no password is required?)

To switch users, I go to the top-right button and choose the entry that says "Switch From <currently logged in user>". Is that what you/your kids are doing? It sounds like you're doing something different.
When I do that, a password box flashes onscreen for a second, but that's just showing that the current user's screen has been locked, and if I ignore it and press nothing, it switches to the login screen a second or two later.

---

### Post by LowSky on 2011-05-27
> **ExileAmongYou said:**
> To switch users, I go to the top-right button and choose the entry that says "Switch From <currently logged in user>". Is that what you/your kids are doing? It sounds like you're doing something different.
When I do that, a password box flashes onscreen for a second, but that's just showing that the current user's screen has been locked, and if I ignore it and press nothing, it switches to the login screen a second or two later.

I'm running a SSD so things go by quickly but the screen does black out for a sec before going to the login screen.

---

### Post by jorritTyb on 2011-05-27
> **ExileAmongYou said:**
> To switch users, I go to the top-right button and choose the entry that says "Switch From <currently logged in user>". Is that what you/your kids are doing? It sounds like you're doing something different.
When I do that, a password box flashes onscreen for a second, but that's just showing that the current user's screen has been locked, and if I ignore it and press nothing, it switches to the login screen a second or two later.

Actually what they do is select the different user directly. i.e. they dont select 'Switch From' but instead they select the menus below that one that indicate the users to switch too. I haven't tried to use the 'Switch From' but it would be nice if they could just use the user directly (as the menus indicate).

Greetings,

---

### Post by jorritTyb on 2011-05-27
Basically here is the list of actions they have to do:

- Select the different user (not the Switch From menu) in the top right (what I would have hoped is this directly switches to the right user but instead the following happens):
- The screen goes black.
- They go to the login screen in which the new user is already set.
- From this login screen they either have to type their password (which is stupid since I added the users so they didn't have to do a password) or else press the 'Switch User' button again.
- Screen goes black.
- A list of users appear and there they have to select the other user again.
- Screen goes black.
- Switch is done.

Greetings,

---

### Post by larsola on 2011-06-22
> Hi, I'm trying to configure ubuntu 11.04 for my children so each of them has a different user. I already added the users and made sure no password is needed at login. However, the switch remains annoying. When one of my children is busy and then another one wants to do something he/she selects the right user in the top-right button. Things brings down the login dialog for that user again. That in itself is already annoying (why is that window shown when no password is required?) but then how does he/she go on from here? You can't simply login as then it will say the password is required. So he/she has to press 'Switch User' again and then select his/her username again. And only then is the switch complete. This is an awful lot of steps for simply switching users. Any way to make this faster?

I'm annoyed by the same thing. My wife and I has different users on the same computer. As it is just used for random Internet browsing we prefer to have automatic login. The automatic login works perfectly as log as the we switch to a user that is not currently logged in. We're normally doing this using the switch to <user> option. But as soon as we switch to a user currently logged in the enter password dialog appears and some extra click and waiting is required to switch the user. I see this as a bug and was going to file a bug report, but I'll wait for a while to see if a solution pops up her.

---

### Post by wildmanne39 on 2011-06-22
Hi, the reason it goes to the login screen it has to log out the previous user and so when the other user logins it the desktop will have that users settings, that is why is has to log out to create the new users settings.

---

### Post by jorritTyb on 2011-06-22
> **wildmanne39 said:**
> Hi, the reason it goes to the login screen it has to log out the previous user and so when the other user logins it the desktop will have that users settings, that is why is has to log out to create the new users settings.

Yes, it has to log out. But it doesn't have to present a login screen when I choose 'Switch to <whatever user>' from the menu as that <whatever user> has no password set. So the login screen is not necessary. Of course it has to log out the current user but I'm annoyed at that unneeded login screen.

Greetings,

---

### Post by larsola on 2011-06-22
Both my wife and I have passwords set, but the account is set to not require a password for login. It always works, except when swapping to directly from one user to another when the second user is already logged.

---

### Post by mastablasta on 2011-06-22
isn't it possible to create multiple users in browser only?
 
I know that Firefox in windows can have multiple users (profiles). i have it liek that at home on XP. my wife any i each have our own account in firefox and to switch them you just need to turn off the browser and start it up again. we have 5 accounts for thunderbird (all in same user).: [http://support.mozilla.com/en-US/kb/Managing-profiles](http://support.mozilla.com/en-US/kb/Managing-profiles)
 
ah here is how you do it in linux: [http://kb.mozillazine.org/Profile_manager](http://kb.mozillazine.org/Profile_manager)
 
KISS principle

---

### Post by grahammechanical on 2011-06-22
Surely the answer is for one user to log out before you switch users. You want to switch already logged in users without needing a password when switching back to that user. That would defeat the purpose of having users in the first place. The new user could simply switch to the previous user and get access to their account. Why have user accounts in the first place? If that is the way you want to work.

This operating method lets you simply switch users without needing to log out but at the same time securing the user's account from unauthorized access. And when you log back in your desktop is restored. Is this not so? This is a neat trick in my opinion.

Regards.

---

### Post by jorritTyb on 2011-06-22
> **grahammechanical said:**
> Surely the answer is for one user to log out before you switch users. You want to switch already logged in users without needing a password when switching back to that user. That would defeat the purpose of having users in the first place. The new user could simply switch to the previous user and get access to their account. Why have user accounts in the first place? If that is the way you want to work.


At home we use our user account to store our personal settings. Not for security. We don't need/want passwords. But we each have our own home dir with files and personalized backgrounds and browser with personalized bookmarks. And it is for that reason we want to switch easily. So we just want to be able to switch and ignore passwords (which we haven't set anyway so why does it insist on asking for something that we don't have?)

Greetings,

---

### Post by mastablasta on 2011-06-23
you can set it with no password? i dont' think so. even "no password" is password.
 
user passwords are there to protect the user from viruses and malware. it needs user confirmation if it wants to access root files.
 
although with autologging enabled there should be some way of easilly switching users.
 
edit: it seem there used to be something called: fast-user-switch-applet for older versions of Ubuntu. perhaps it might still work.

---

### Post by larsola on 2011-06-23
I've tried various applet in previous versions without luck, so I was hoping that a clean install with 11.04 would fix it. Sadly it didn't. I'm not considering this as a big thing, but it would be nice if it worked!

---

### Post by lscheres on 2011-07-18
I too would love to directly switch users(Click another user from the log out/shutdown menu) and not have to type in a password, as i me and my girlfriend dont need that extra bit a security and its just and extra 2 steps i dont think should be necessary. Its fine if i click log out then switch but thats still an extra step or two that shouldn't be needed. Why can't someone make a script to auto enter password and log in automotically when you click on a user, im not a crazy linux coder so i don't have that ability

---

### Post by larsola on 2011-07-19
I still think it's a bug, but since it's been like this "forever" I suspect that the priority is low (as it is compared to many other things) and the resources needed to fix it doesn't match the gain.

---

### Post by kitchens on 2011-10-11
I've had this same issue for a long time but I've just lived with it. In 11.04 I was able to switch users by going to the login screen rather than directly choosing the other user on the little user switcher app. In 11.10 it is completely broken. I have to enter a password no matter what. Hope there is a solution to this or I'll just stick to 11.04

---

