---
title: "Password ajusting"
date: 2009-12-02
forum: General Help
---

### Post by mikemikemike on 2009-12-02
I am relatively new to Linux, and yes I have used the nifty search function but either there is no solution or I do not the proper syntax for the search anway..


These aren't actual passwords. 

My issue is this. In terminal, I have successfully changed the root (su) password to "Red". My normal accounts password is "Blue".  I run a program and it asks me to Authenticate " Authentication is required to install software packages...". It only accepts my account password.

My issue is that this is a family computer and I do not want anyone accidentally installing anything. Is there a way to change the password for these prompts to either "Red" or just something other than the profile password?


Thanks in advance,
Mike

---

### Post by fluffman86 on 2009-12-02
If you don't want someone installing something, they should not be logged in as an administrator, and should not have admin priviledges.

User "mike" should be an admin, and noone should know his password.
User "dad" should be a Desktop user, and only he should know the password to that account, but it doesn't really matter since he can't change anything.

Set it all up in System > Admin > Users and Groups.

---

### Post by mikemikemike on 2009-12-02
So the user created at install is by default an Admin?

With this account I cannot even create a user. How can this be an admin. The only thing I see checked, that I would think may need to be unchecked Administer the system under privileges.

---

### Post by bwang on 2009-12-02
Try System>Administration>Users and Groups

---

### Post by mikemikemike on 2009-12-03
Ok I think I made a boo-boo and need help. 

I deleted the Family account. However the folder is still there. I tried recreating it but it says it already exists. What do I do now?


and when I try 
sudo userdel -r

user doesn't exist


maybeeee I'll try a good old reboot. Most simple of all just came to mind.

---

### Post by mikemikemike on 2009-12-03
Update.

No reboot did not help one bit.

Further update. Even though account Mike is admin, I was unable to delete the account folder under home. Why?


I logged in Terminal as root. ran rm -rf /home/family/ all gone was able to create new account.

---

### Post by mikemikemike on 2009-12-09
I have one more password question. Is there a way for me to execute programs in th GUI on another account with my credentials?

---

### Post by lisati on 2009-12-09
> **mikemikemike said:**
> Ok I think I made a boo-boo and need help. 

I deleted the Family account. However the folder is still there. I tried recreating it but it says it already exists. What do I do now?


and when I try 
sudo userdel -r

user doesn't exist


maybeeee I'll try a good old reboot. Most simple of all just came to mind.
I think the "add new user" process gets confounded by the presence of the folder. If there's nothing important in the folder, you can probably delete it safely then try adding the user again.

---

### Post by nothingspecial on 2009-12-09
> **mikemikemike said:**
> I have one more password question. Is there a way for me to execute programs in th GUI on another account with my credentials?

I don`t know about all gui`s but if my son wants to install a game from software center I can just type my password in his account.

---

### Post by derrick81787 on 2009-12-09
> **mikemikemike said:**
> I have one more password question. Is there a way for me to execute programs in the GUI on another account with my credentials?

There is a GUI way, but I don't remember what it is, and I'm at work right now and can't check.  In old versions of Ubuntu there was a "Run As User" or something like that under the System category on the Application menu.  Now, on a default install, there is nothing in the System category, and so it doesn't even show up.  You might try looking under "Administration."  That's most likely where it was moved to.

If it isn't that important to you to use all GUI, you might be able to do this using sudo (or gksudo if you want a dialog box for your password).  Type "man gksudo" or "man sudo" in a terminal to see more information about that.

---

### Post by mikemikemike on 2009-12-20
> **nothingspecial said:**
> I don`t know about all gui`s but if my son wants to install a game from software center I can just type my password in his account.


That is exactly what I want to do, but with every prompt. There are many windows that prompt for admin password. My password and my root password do not work. Than I type in the family account password, it accepts it but says I do not have the rights.


The only time I am able to use my password on another account is, as stated above, installing programs from software center.   I want to be able to have it work like this all the time. Its a royal PITA to have to log into my account just to make a small change.

---

### Post by bodhi.zazen on 2009-12-20
What you are asking for is possible, I do it all the time. You may manage users and passwords via a GUI interface as well.

You have posted so much information, however, and you have made so many adjustments to your system, I am not sure how to advise you.

First piece of advice, do not change the default behavior if you do not understand how the system works. Specifically, you give me the impression you set a root password which was not necessary. It also appears you deleted accounts without understanding the syntax =)

The man pages are your friend, it is extremely useful to learn to read them. Or ask here if you do not understand, but please include additional information so we know exactly what you have done.

I suggest you start with this page :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 

I then suggest you understand what Linux permissions mean and how they work.

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

If you stay with the default behavior, when you run an application that requires administrative (root) privileges, you will get an authentication box. Select your admin user (form the pull down menu) and enter your admin users password.

If you really want to change how it all works, you will need to understand how to configure sudo:

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

[http://www.sudo.ws/sudo/man/sudo.html](http://www.sudo.ws/sudo/man/sudo.html)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

As you can see from those links, sudo is very flexible and you may configure a number of options.

---

### Post by mikemikemike on 2009-12-28
Sorry its taken so long to respond, but why does it only work half the time? This is what is confusing me.

---

### Post by t0p on 2009-12-28
> **mikemikemike said:**
> Sorry its taken so long to respond, but why does it only work half the time? This is what is confusing me.

Can you please explain what exactly you mean by "it only works half the time"?  *What* works only half the time?  What happens the other half of the time, when it doesn't work?

Your post is extremely vague and is meaningless without clarification.

---

### Post by mikemikemike on 2010-01-02
Only half of the time does it prompt for my password on another users account when performing and action that is not authorized.

---

### Post by bodhi.zazen on 2010-01-03
> **mikemikemike said:**
> Only half of the time does it prompt for my password on another users account when performing and action that is not authorized.

And are you aware that with sudo, once you enter your password, there is a "grace period" where you do not need to re-enter your password. The default is 15 minutes.

from [http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

> 
**timestamp_timeout**  Number of minutes that can elapse before **sudo** will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

---

