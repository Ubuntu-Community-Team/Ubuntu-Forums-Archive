---
title: "User Account Set Up"
date: 2012-01-18
forum: General Help
---

### Post by sofatiger51 on 2012-01-18
Hi,

I am new to Ubuntu and would like to learn more how to use the OS better and more efficiently. I recently upgraded to Ubuntu 11.10 from 11.04. After installation and updates and installed all the programs that I needed, I try to create a standard user. 

Going through User Account set-up, after authenticating by adding standard user account,
the new user was added with no provision for password creation. Is this a bug? How do I overcome this? 

In the past, I remembered when creating one standard user account, there is always provision for password set up for new standard user account. My experience now is I cannot add a standard user account. 

Any help will be highly appreciated:D.

---

### Post by Savio2010 on 2012-01-18
in the dash search type User Accounts.

Click the plus button to add a new user. (you need to type the sudo password)

---

### Post by sofatiger51 on 2012-01-18
> **Savio2010 said:**
> in the dash search type User Accounts.

Click the plus button to add a new user. (you need to type the sudo password)
I enter sudo password to add standard user. The problem is when adding new standard user account, it has no provision for me to create password for new standard user account.

The new user was added successfully after authenticating with sudo password. When I switch over, standard user does not work. I could not sign in because I have no password because during the creation of standard user, Ubuntu does not provide me to create password for new standard user account.

This is not a problem with previous Ubuntu distros (11.04 /10.10/10.04). In the previous Ubuntu, creating new user account always followed by password creation for new user but not with Ubuntu 11.11 :D.

---

### Post by GraeW on 2012-01-18
I have to pull up my laptop to doublecheck, but I remember adding users to my fresh 11.10 install. You actually create them, then you have to click on the sentence next to the "Password" line to create a password for that account. I can't recall if there also was another step to actually activate the account though.

---

### Post by sofatiger51 on 2012-01-18
> **GraeW said:**
> I have to pull up my laptop to doublecheck, but I remember adding users to my fresh 11.10 install. You actually create them, then you have to click on the sentence next to the "Password" line to create a password for that account. I can't recall if there also was another step to actually activate the account though.

:DThanks for your reply. That is the problem. When I started up user account through Dash Home, I managed to add standard user account through authenticating sudo password. There are no other line with password to create password line. The user account just added. Does Ubuntu as snip utility like Windows 7 that I can use so that I can show you exactly the picture of user account creation. This is weird for Linux Ubuntu to be behaving like windows with no respect for security omitting password creation step.

Perhaps I should re-install Ubtuntu 10.04 and stick with it. I personally don't like Unity and I am not much fun of Gnome 3 shell either. With 10.04, I have no problem with user account creation at all and I like the Gnome 2.:P

---

### Post by GraeW on 2012-01-18
I pulled out the laptop and started it up during lunch.
 
Log into your Ubuntu, start up "System Settings" and select "User Accounts" .. on the right side near the top is an "unlock" button.. click on that and enter your password for SU access. In the list of users you should see the account you created - if so, click on that user name and you will see the information on the right side. Below "Login Options" is Password (which should say "Account Disabled") and then the Automatic Login toggle. Just click on the "Account Disabled" line and it will bring up a password dialog. If for some reason that new user account you created doesn't show, just start a new one (the + sign in the lower left).
 
I'm also not fond of the Gnome/Unity thing going on, so usually use XFCE. I installed Ubuntu as the base so have to sometimes go back to the G/U to get some admin things done (I couldn't find the User Accounts option in XFCE's system settings). When 12.04 hits, I will probably just wipe and install Xubuntu.
 
Hope this helped!

---

