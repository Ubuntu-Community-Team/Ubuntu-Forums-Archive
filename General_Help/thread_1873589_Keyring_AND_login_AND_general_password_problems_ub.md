---
title: "Keyring AND login AND general password problems ubuntu 11.10"
date: 2011-11-01
forum: General Help
---

### Post by kilpikonna on 2011-11-01
Find this very frustrating. Several things:

1. I have autologin turned "off", so at startup I have to click my username, but ubuntu doesn't ask me any password, it just logs in. Eventhough I have a password set for my account and autologin turned off! Why it does not require the password?

2. If I choose autologin "on" AND try to remove my administrator password, suddenly the system doesn't accept any passwords when installing programs or even trying to "unlock" my user account to change settings. It says my password is not valid. I can correct this by typing to terminal "passwd" and then just write new password. But the problems remains when removing the password again.

3. When I just tried to change password at user accounts page, the program just hangs and is not responding currently at all. 

4. I get prompted for "keyring password" everytime I login. I've searched google and tried all the solutions I've found, but they never work. My keyring password is the same as my login password, so there should be no problems. I just feel the whole password system is bugged in this version of ubuntu.

Any solutions?

---

### Post by aocislucid on 2011-12-06
I am having a similar problem...  I had just installed 11.10 on my HP laptop and sudo wasn't accepting my password (yes I know it's not supposed to appear as one types... it told me the password I had set was wrong).  So thinking of possible solutions, I decided to remove the password... Bad idea.  I still can't do what I need to do in sudo (java) and now I can't create a new password because I need to unlock the dialogue to make changes to my user account. Autologin is turned off.

Sorry, I'm not trying to steal your thread; I just believe that we are in the same boat with the whole buggy password issue :?

---

### Post by DMWill on 2011-12-09
hey guys, my problem is almost identical to what it sounds like you're dealing with.  like aocislucid, i removed my password to try out not needing to enter it when logging in.  didn't like it so much, but then i couldn't enter a new one.  however if you login to one of the CRTL+ALT+FN consoles and ```
sudo passwd <username>
```it will ask you to enter a new password.  this works to give back the use of apt and anything else that requires a password to get into.  bad news though, this does not then require a password at login like i was hoping it would.  so i'm kinda in the same boat as you guys and although it's not a big deal to not enter my password to login (actually kind of convenient) i would love to know why i can't figure out how to put it back the way it was.

---

### Post by oldtimer7777 on 2011-12-09
In System Settings go to "User Accounts", then click "Unlock", enter  your password and click the button next to "Automatic Login" so that it prompts you for a password during login.

> **DMWill said:**
> hey guys, my problem is almost identical to what it sounds like you're dealing with.  like aocislucid, i removed my password to try out not needing to enter it when logging in.  didn't like it so much, but then i couldn't enter a new one.  however if you login to one of the CRTL+ALT+FN consoles and ```
sudo passwd <username>
```it will ask you to enter a new password.  this works to give back the use of apt and anything else that requires a password to get into.  bad news though, this does not then require a password at login like i was hoping it would.  so i'm kinda in the same boat as you guys and although it's not a big deal to not enter my password to login (actually kind of convenient) i would love to know why i can't figure out how to put it back the way it was.

---

### Post by mcduck on 2011-12-09
I suppose the prolems you are having is because there are actually two options regards the password usage at login time:

*The Login screen settings* allows you to set automatic login for certain user. This will just skip the login screen completely and log that user in automatically.

*User settings* includes option to set the user to not require a password to log in. This will still show the login screen, so you can switch beween different users, it simply doesn't ask for the password.

(Of course either way will require you to input your keyring password to unlock it, unless you have set the keyring to use empty password. It's only automatically unlocked if you actually use a login password and that password matches the keyring password).

...and tryign to remove the need for a password by setting your admin password to empty will definitely cause troubles (and also plenty of security issues). You *must* have that password, even though you may configure certain things to not ask for it.

---

### Post by DMWill on 2011-12-09
@oldtimer7777 - Automatic Login is already set to off.  the problem is not that it skips the login screen after boot.  at the login screen, there's a button that says Login instead of a password box.  i appreciate the suggestion though.

@mcduck - that description basically boils down the situation.  i completely understand what you're saying.  11.04 used to have a box you would tick to have the option whether to require the password at login or not.  hopefully it's not just me, but my user account settings dialog no longer has that box in 11.10.  i would just like to know where that was moved to, or a possible way to reset the login options without seriously messing up anything important.

thanks guys

---

### Post by oozienelson on 2011-12-26
I'm having the same problem. Autologin is disabled and my account has a password, but on the login screen there is no password prompt, just a login button that logs me in without asking for a password. Has anyone made any progress on this?

---

### Post by oozienelson on 2011-12-28
I managed to solve the problem by installing Xubuntu desktop and changing the settings in Users and Groups.

---

### Post by irpsit on 2011-12-31
I have the same problem.

When I boot the system, it shows different users, and when I choose one, they login without asking for the passport.

This remains even when going to users settings and and disable auto login. 
I believe that this can compromise the security of the system.

The file sudo nano /etc/lightdm/lightdm.conf shows this:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu-2d

Does anyone know a solution?

I created a new administrator user, and now this one prompts for a password at login, but still the other users don't ask for a password. And I don't want to remove them, because I have a lot of settings there that I don't want in this newly created user.

---

### Post by irpsit on 2011-12-31
I manage to solve partially the problem by doing a very funny trick. Let's see if I remember it well, because it was all a bit confusing, but I guess you will figure out the trick.

I had username A. And it was not asking for password, even with autologin disable.

I think you cannot disable autologin for A, when you are logged inside A.

So I created a new user, let's call it B, and set up a password for it.

Then I login with B and went to user settings and I changed the login settings for A; I chose login without a password. Then I guess I did a log out, login in B again, and went again to the settings and defined a new password for A (while working in B desktop).

Now, log out B and login A, it will ask the password.

I am not sure if I remember these steps correctly, but this was what I did more or less. 


> **irpsit said:**
> I have the same problem.

When I boot the system, it shows different users, and when I choose one, they login without asking for the passport.

This remains even when going to users settings and and disable auto login. 
I believe that this can compromise the security of the system.

The file sudo nano /etc/lightdm/lightdm.conf shows this:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu-2d

Does anyone know a solution?

I created a new administrator user, and now this one prompts for a password at login, but still the other users don't ask for a password. And I don't want to remove them, because I have a lot of settings there that I don't want in this newly created user.

---

### Post by irpsit on 2011-12-31
However, I still have this message showing up, after login

Enter password for keyring 'Default' to unlock 
An application wants access to the keyring 'Default', but it is locked

Then, I type command rm ~/.gnome2/keyrings/default.keyring
And message will be gone

---

