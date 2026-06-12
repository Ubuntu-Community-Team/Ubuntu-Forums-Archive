---
title: "No password on login"
date: 2009-12-22
forum: General Help
---

### Post by DavidFourer on 2009-12-22
I want to login without a password, or have a blank password, in Karmic.  I see old posts on this, but they dealt with 2-3 year old versions of Ubuntu.  I suspect things have change.

Under System>Help and Support (Gnome Display Reference manual / Security / PAM) I found this:
> If the computer is used by several people, which makes automatic login unsuitable, you may want to allow some users to log in without entering their password. This feature can be enabled as a per-user option in the users-admin tool from the gnome-system-tools; it is achieved by checking that the user is member a Unix group called "nopasswdlogin" before asking for a password. For this to work, the PAM configuration file for the "gdm" service must include a line such as:
      gdm auth  sufficient  pam_succeed_if.so  user ingroup nopasswdlogin

I don't know what the "PAM configuration file" is.  Under System>Admin>users-and-Groups, I created a group "nopasswordlogin."  This group disappeared after logging out and in again.  

This is all rediculously complicated.  Why is the option "Don't ask for password on login" faded out in the first place? (Sys>admin>users-and-groups>click-on-keys>edit user)  Please tell me there is a simple way.

---

### Post by starcraft.man on 2009-12-22
System > Admin > Login Screen > Log in as X Automatically.

Just don't use machine in a public place if it's important files on it.

---

### Post by howefield on 2009-12-22
Have you tried going into System > Administration > Login Screen ?

Click on the unlock button, type in your password, check the radial button next to Log in as "user" automatically. Select the account and the rest should be obvious.

---

### Post by dasy2k1 on 2009-12-22
changing it to autologin is much better than having a blank password, 

when you need to do somthing with root privileges this will still prompt you for your password which is a good thing!

---

### Post by DavidFourer on 2009-12-22
Thanks for the quick reply.  This works.  

I have to turn off ubuntu-one on start-up because it wants access to the default keyring.  That's OK since I was only playing with ubuntu-one

Then the NewtorkManager asks for access to the wep 128 key.  I don't need that, since it's a desktop computer with a wired connection normally.  I know there is a simple way to not start up wifi on start-up, but I can't seem to find it.

I wonder what else will ask for access to the keyring?  I may just stick with logging in.  I'll experiment.

Thanks.

---

