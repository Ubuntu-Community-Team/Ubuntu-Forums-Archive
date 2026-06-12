---
title: "Incorrect Password"
date: 2009-12-17
forum: General Help
---

### Post by gglaser on 2009-12-17
Hi, I have been using my Ubuntu 8.4 machine fine for awhile, but all of a sudden, I seem to be locked out of my existing terminal session. 
 
"sudo" commands don't accept my password. (I get the messages "sorry, try again" and "sudo: 2 incorrect password attempts.") If I try "su" and type my password, I get "Authentication failure." If I try to start a new terminal session over SSH and enter my password, I get "Access denied." 
 
I am sure that I am entering the correct password, and I know this isn't an issue with Caps Lock, Num Lock, etc. I am also entering my own user password for "sudo," not the root password. It seems that somehow I am locked out of my account. Does anyone know how this might have happened and how I can fix it?
 
Thank you!
gglaser

---

### Post by Darael on 2009-12-17
I don't know how it might have happened, but I **can** tell you how you should be able to fix it!

If you reboot, one of your options at GRUB will be "recovery mode" (you might have to press escape to get the menu). Of the options this will present you with after it boots, you will want to choose to drop to a root shell. Then you can reset your user password with "passwd <username>", to ensure it's what you want it to be. Finally, to make sure you're still allowed to sudo, run "groups <username>" and see if one of the items listed is "admin", and if not, run "adduser <username> admin". Finally, reboot (if the command "reboot" doesn't work, use "shutdown -r now" instead).

HTH.

---

### Post by Fiddler85 on 2009-12-17
Darael, may I ask you for a complete breakdown of how to do this?  I am new to ubuntu, and bought a compaq presario F700 second-hand and cannot change any of the settings because of not knowing the password.  Would this procedure you mentioned above fix that?  Really appreciate the help!

---

### Post by ubudog on 2009-12-17
> **Fiddler85 said:**
> Darael, may I ask you for a complete breakdown of how to do this?  I am new to ubuntu, and bought a compaq presario F700 second-hand and cannot change any of the settings because of not knowing the password.  Would this procedure you mentioned above fix that?  Really appreciate the help!

This might be useful to you: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")  Hope that helps.:)

---

### Post by Darael on 2009-12-17
The procedure I suggested above will let you change your password (preferably to what it was before) so that you can log in. Here's a complete breakdown (note that any commands in "quotes" should be entered without them!):

1) reboot
2) a) if you get "GRUB loading... press ESC to show the menu", press escape.
b) if not, ignore that step.
c) Select the uppermost of the options of the form "Ubuntu, linux 2.2.28-xx-generic (recovery mode)" (or similar)
3) When presented with a list of options, choose "root" or "Drop to root shell".
NOTE: for the following, substitute <user> with your username.
4) Type "passwd <user>" and hit return
5) Type your "new" password and hit enter. Don't worry about it not showing each character.
6) Type your "new" password again. Hit enter.
7) Type "groups <user>". Press enter.
8) If one of the words you get as output is "admin", skip to step 10
9) Type "adduser <user> admin"
10) Type "shutdown -r now"
11) Log in to your system when it reboots.

That ought to work!

---

### Post by Darael on 2009-12-17
> **ubudog said:**
> No, the above procedure would just add the user to the admin group.  This might be useful to you though: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")  Hope that helps.:)
I beg to differ - I began by suggesting resetting the user password!

---

### Post by ubudog on 2009-12-17
> **Darael said:**
> I beg to differ - I began by suggesting resetting the user password!

Yes, I am sorry.

---

### Post by Fiddler85 on 2009-12-17
Thank you SO much for your help!!  It worked!  I really do appreciate it! Thank you!

---

### Post by gglaser on 2009-12-21
Thanks for the replies, but ...  When I tried a few hours later, I was able to successfully login over SSH.  I didn't try any of the password change steps that you suggested, and I know that I was entering the same password as before.  It seems that somehow my account had gotten locked for a short period of time and started working again after some period of time.  Does anyone know how this could happen?  I don't think I had several unsuccessful password entries at the beginning.
 
Thanks,
gglaser

---

